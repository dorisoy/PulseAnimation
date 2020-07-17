# PulseAnimation for Xamarin.Forms
Pulse animation for xamarin forms based on SkiaSharp

<html>
<p align="center">
  <img src="https://github.com/dorisoy/PulseAnimation/blob/master/Screenshot.jpg?raw=true" height="1000">
</p>
</html>

------------

# Compatibility 
- Xamarin.Forms

------------

# Quickstart 
##### Xaml
```xml
     <PulseAnimation:Pulse AutoStart="true" 
                      PulseColor="#8e44ad" 
                      Margin="50" 
                      Speed="10"  />
```

Use an image resource as an Embedded Resource
Do not add the image as a resource.  would rather do the following:

    Create the image/icon and save it to a file
    Choose Shared Project -> Add Existing Item and add the file
    Set the Build Action to Embedded Resource

# Dependencies
- SkiaSharp
- SkiaSharp.Views
- SkiaSharp.Views.Forms
