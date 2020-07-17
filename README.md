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
  <?xml version="1.0" encoding="UTF-8" ?>
<ContentView x:Class="DCMS.Client.CustomViews.SpeechView"
             xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:iconize="clr-namespace:Plugin.Iconize;assembly=Plugin.Iconize"
             xmlns:custom="clr-namespace:DCMS.Client.CustomViews;assembly=DCMS.Client"
             xmlns:textRes="clr-namespace:DCMS.Client.Resources">
    <Grid RowSpacing="0"
          ColumnSpacing="0">
        <Grid.RowDefinitions>
            <RowDefinition Height="45" />
            <RowDefinition Height="150" />
            <RowDefinition Height="500" />
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>

        <Label Grid.Column="0"
               Grid.Row="0"
               Text="{x:Static textRes:TextResources.EnableMicrophone}"
               TextColor="{StaticResource PrimaryTextColor}"
               VerticalOptions="CenterAndExpand"
               HorizontalOptions="Start"
               FontFamily="{StaticResource QuickSandBold}"
               Style="{StaticResource H4-Regular}"
               Margin="20,0,0,0" />
        <Switch Grid.Column="1"
                Grid.Row="0"
                x:Name="EnableMicrophoneCommand"
                VerticalOptions="Center"
                HorizontalOptions="End"
                Margin="0,0,10,0"
                OnColor="#53a245"
                ThumbColor="#53a245"
                IsToggled="{Binding EnableMicrophone,Mode=TwoWay}" />

        <Frame Grid.Row="1"
                     Grid.ColumnSpan="2" 
               CornerRadius="10" 
               Margin="20"
               HasShadow="True"
               BackgroundColor="#eeeeee">
            <Label  
                    x:Name="RecognitionText"
                    FontSize="16"
                    Text="{Binding RecognitionText}"
                    HeightRequest="100"
                    Padding="5"
                    HorizontalOptions="Center"
                   VerticalOptions="Center" />
        </Frame>

        <AbsoluteLayout Grid.Row="2"
                        Grid.ColumnSpan="2">
            <!--脉冲动画-->
            <custom:Pulse AbsoluteLayout.LayoutBounds=".5,0,300,300"
                          AbsoluteLayout.LayoutFlags="XProportional"
                          PulseColor="#EEEEEE"
                          Speed="10"
                          VerticalOptions="FillAndExpand"
                          HorizontalOptions="FillAndExpand">
                <custom:Pulse.Triggers>
                    <DataTrigger TargetType="custom:Pulse"
                                 Binding="{Binding EnableMicrophone}"
                                 Value="True">
                        <Setter Property="AutoStart"
                                Value="True" />
                    </DataTrigger>
                    <DataTrigger TargetType="custom:Pulse"
                                 Binding="{Binding EnableMicrophone}"
                                 Value="False">
                        <Setter Property="AutoStart"
                                Value="False" />
                    </DataTrigger>
                </custom:Pulse.Triggers>
            </custom:Pulse>
            
            <!--开始语音识别-->
            <iconize:IconButton AbsoluteLayout.LayoutBounds=".5,0.272,60,60"
                                AbsoluteLayout.LayoutFlags="PositionProportional"
                                Text="{Binding IconCounter}"
                                FontSize="35"
                                HeightRequest="60"
                                WidthRequest="60"
                                Padding="0"
                                Style="{StaticResource AppButtonStyle}"
                                Command="{Binding RecognitionCommand}">
                <iconize:IconButton.Triggers>
                    <DataTrigger TargetType="iconize:IconButton"
                                 Binding="{Binding EnableMicrophone}"
                                 Value="True">
                        <Setter Property="TextColor"
                                Value="#53a245"></Setter>
                        <Setter Property="IsEnabled"
                                Value="True"></Setter>
                    </DataTrigger>
                    <DataTrigger TargetType="iconize:IconButton"
                                 Binding="{Binding EnableMicrophone}"
                                 Value="False">
                        <Setter Property="TextColor"
                                Value="Gray"></Setter>
                        <Setter Property="IsEnabled"
                                Value="False"></Setter>
                    </DataTrigger>
                </iconize:IconButton.Triggers>
            </iconize:IconButton>

        </AbsoluteLayout>
    </Grid>
</ContentView>
```

# Dependencies
- SkiaSharp
- SkiaSharp.Views
- SkiaSharp.Views.Forms
