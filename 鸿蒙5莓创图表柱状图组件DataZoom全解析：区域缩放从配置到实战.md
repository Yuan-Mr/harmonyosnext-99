# HarmonyOS 5 Meichuang Charts Bar Chart Component DataZoom Comprehensive Analysis: From Configuration to Practice

Hello everyone, welcome back to the special session of HarmonyOS 5 Meichuang chart components. In this issue, we will explain the detailed usage of the area zoom (dataZoom) function. Area zoom is a very practical function in data visualization, which can help users focus on data in a specific interval, especially suitable for scenarios dealing with large amounts of data or requiring detailed analysis. The following will be explained one by one from six dimensions: attribute function, type, default value, optional range, applicable scenarios, and code examples.


### 一、show Attribute

**Function**: Control the display and hiding of the area zoom component  
**Type**: Boolean  
**Default Value**: false (not displayed by default)  
**Optional Values**: true (display) / false (hide)  
**Usage Scenario**: When the data volume is large (such as more than 10 items), it is recommended to enable this function, allowing users to zoom in and view local data through sliding or pinching gestures.  
**Code Example**:
```
dataZoom: {
  show: true,  // Enable the area zoom component
  start: 2,
  end: 8
}
```


### 二、start Attribute

**Function**: Set the starting index of the initial display range of the area zoom  
**Type**: Number  
**Default Value**: 0 (start from the first data item)  
**Optional Range**: Integers from 0 to the total data length minus 1  
**Usage Scenario**: When you need to display the middle part of the data by default (such as skipping the first few abnormal data), you can specify the starting position by setting start.  
**Code Example**:
```
dataZoom: {
  show: true,
  start: 3,     // Start displaying from the 4th data item
  end: 10
}
```


### 三、end Attribute

**Function**: Set the ending index of the initial display range of the area zoom  
**Type**: Number  
**Default Value**: 6 (display the first 7 data items by default)  
**Optional Range**: A value must be greater than start and not exceed the total data length  
**Usage Scenario**: Combine with the start attribute to achieve "default focus on a certain segment of data", such as displaying the middle 5 days of the recent 7 days of data.  
**Code Example**:
```
dataZoom: {
  show: true,
  start: 5,
  end: 11      // Display the 6th to 12th data items
}
```


### 四、velocity Attribute

**Function**: Control the scrolling speed during manual sliding  
**Type**: Number  
**Default Value**: 0 (use the built-in default speed of the component)  
**Optional Range**: It is recommended to use floating-point numbers between 0 and 1. The larger the value, the faster the scrolling.  
**Usage Scenario**: When the data volume is extremely large (such as more than 1000 items), appropriately increasing the speed can improve the interaction experience.  
**Code Example**:
```
dataZoom: {
  show: true,
  velocity: 0.5  // Medium scrolling speed
}
```


### 五、num Attribute

**Function**: Limit the maximum number of data entries displayed in the visible area  
**Type**: Number  
**Default Value**: 0 (automatically calculated based on the container width)  
**Optional Range**: Integers greater than or equal to 1  
**Usage Scenario**: Forcefully constrain the number of displayed entries (such as fixing 7 entries in the dashboard scenario) to avoid fluctuations in the number of displayed entries due to changes in the container size.  
**Code Example**:
```
dataZoom: {
  show: true,
  num: 7        // No matter how you zoom, at most 7 entries are displayed
}
```


### 六、Complete Comprehensive Case

```
@State dataZoomOption: Options = new Options({
  xAxis: {
    data: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
  },
  dataZoom: {
    show: true,        // Enable zoom
    start: 3,          // Default start from April
    end: 8,            // Default display until September
    velocity: 0.3,     // Gentle scrolling speed
    num: 6             // At most 6 months are displayed
  },
  series: [{
    name: 'Sales',
    data: [120, 200, 150, 80, 70, 110, 130, 180, 95, 88, 160, 210]
  }]
})
```

**Effect Description**: By default, the data from April to September is displayed. Users can slide to view other months, but no matter how they zoom, the interface displays at most 6 months of data at the same time, and the sliding process has a smooth animation effect.


### Conclusion

This issue ends here. I hope you can use the dataZoom component to achieve more flexible data display control. If you encounter boundary value problems in actual use, remember to check whether the value range of start/end is legal. In the next issue, we will deeply explain the advanced skills of dynamic data update. Stay tuned!
