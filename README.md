[![bitHound Score](https://www.bithound.io/github/rajeshwarpatlolla/ionic-timepicker/badges/score.svg)](https://www.bithound.io/github/rajeshwarpatlolla/ionic-timepicker)

##Introduction:

This is a `ionic-utc-timepicker` bower component which can be used with any Ionic framework's application.

##Prerequisites.

1) node.js, npm, ionic, bower and gulp.

##How to use:

1) In your project repository install the ionic time picker using bower


2) Give the path of  `ionic-timepicker.bundle.min.js` in your `index.html` file.

````html
<!-- path to ionic/angularjs js -->
<script src="lib/ionic-timepicker/dist/ionic-timepicker.bundle.min.js"></script>
````    

3) In your application module inject the dependency `ionic-timepicker`, in order to work with the `ionic-timepicker` component

````javascript
angular.module('modulename', ['ionic', 'ionic-timepicker']){

}
````

4) Use the below format in your template's corresponding controller

````javascript
$scope.timePickerFromObject = {
  step: 15,  //Optional
  format: 12,  //Optional
  titleLabel: '12-hour Format',  //Optional
  setLabel: 'Set',  //Optional
  closeLabel: 'Close',  //Optional
  setButtonType: 'button-positive',  //Optional
  closeButtonType: 'button-stable',  //Optional
  callback: function (val) {    //Mandatory
    timePickerCallback(val);
  }
};
````

**$scope.timePickerObject** is the object, that we need to pass to the directive. The properties of this object are as follows.

**b) step** (Optional) : This the minute increment / decrement step. Default value is `15`

**c) format** (Optional) : This the format of the time. It can can two values i.e.`12` or `24`. Default value is `24`

**d) titleLabel** (Optional) : The `Title` for the popup. Default value is `Time Picker`

**e) setLabel** (Optional) : The label for the `Set` button. Default value is `Set`

**f) closeLabel** (Optional) : The label for the `Close` button. Default value is `Close`

**g) setButtonType** (Optional) : This the type of the `Set` button. Default value is `button-positive`. You can give any valid ionic framework's button classes. 

**h) closeButtonType** (Optional) : This the type of the `Close` button. Default value is `button-stable`. You can give any valid ionic framework's button classes.

**i) callback** (Mandatory) : This the callback function, which will get the selected time in to the controller. You can define this function as follows.
````javascript
function timePickerCallback(val) {
  if (typeof (val) === 'undefined') {
    console.log('Time not selected');
  } else {
    var selectedTime = new Date(val * 1000);
    $scope.temp.fromtime = new Date(selectedTime.setMinutes(selectedTime.getMinutes()-330));
    $scope.timePickerFromObject.fromtime=$scope.temp.fromtime;
    //console.log('Selected epoch is : ', val, 'and the time is ', selectedTime.getUTCHours(), ':', selectedTime.getUTCMinutes(), 'in UTC');
  }
}
````

5) Then use the below format in your template / html file

````html
<ionic-timepicker input-obj="timePickerFromObject">
  <button class="button button-small button-outline button-assertive overflowShow" >
    <standard-time-meridian etime='temp.fromtime'></standard-time-meridian>
    <span ng-hide="temp.fromtime">Select time</span>{{temp.fromtime | date:'hh:mm a'}}
  </button>
</ionic-timepicker>
````

**a) ionic-timepicker**  is the directive, to which we can pass required vales.

**b) input-obj** (Mandatory) : This is an object. We have to pass an object as shown above.

##Screen Shots:

![12-Hour](https://lh6.googleusercontent.com/-UL18wuskI_A/VNHkGj8tdwI/AAAAAAAADdU/5tBbZcF6_es/w328-h494-no/TimePicker-1.jpg "12-Hour")
![24-Hour](https://lh5.googleusercontent.com/-xgqgH2zRSuA/VNHkGQ6R8cI/AAAAAAAADdQ/5gGJ1nUqmA0/w328-h494-no/TimePicker-2.jpg "24-Hour.")
