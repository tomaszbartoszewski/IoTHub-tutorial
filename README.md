## Welcome to Azure IoT Hub tutorial

This tutorial can be followed on it's own, but I created it as additional material for my talk "Saving the World with IoT", so after watching the presentation, it's easier to do it at home.

### What we are going to do?

The plan is to create an IoT Hub, add a device (run the code in Console App) which will send temperature reading. We want to process telemetry (measurements and data from device) and based on this information send commands to device. And all of that for free.

### Prerequisites

If you don't have an Azure account already, create it https://azure.microsoft.com/en-gb/free/
We will use Visual Studio Code for generating code and editing it https://code.visualstudio.com/

### Create IoT Hub

Pick from the list of options IoT Hub, if you haven't created any IoT Hub before, the list will be empty. Press Add button or Create IoT hub.

![Create IoT Hub](images/Create_IotHub.png)

On basic screen pick your subscription, resources, location and the IoT Hub name, don't finishe yet, as we have to change scale tier.

![Create IoT Hub, Basic](images/Create_IotHub_Basic.png)

When you set all the values, go next to Size and Scale part, by default S1 will be selected. We want to use F1: Free tier, it allows you to send 8000 messages per day without paying anything. You are allowed to have only one IoT Hub with this tier, so make sure that you don't run our of messages per day while testing your application.

![Create IoT Hub, Size and Scale](images/Create_IoTHub_SizeAndScale.png)

You can press Review + create, make sure all the values are as expected and press Create. It will take about 2 minutes to provision it.

### Create first device

Once IoT Hub is created, we can add our first device. Select your IoT Hub and go to the Explorers sections and press IoT devices. You can see there blue Add button, press it to create a device.

![Create first device](images/Create_Device.png)

For out case we just have to give our device Id, usually it would be some autogenerated unique value, but to make it easy, we will call it "bedroom".

![Create first device, set name](images/Create_Device_Properties.png)

Press Save and device will be created. You can see it on the list.

![Create first device, list of devices](images/Create_Device_Created.png)

We have everything ready to connect from code, you could write it on your own. To make it easier, we will use VS Code pluggin to generate it.

### Connect from Visual Studio Code

We want to install extension for VS Code called Azure IoT Hub Toolkit.

![VS Code, IoT Hub Toolkit](images/Azure_IoT_Hub_Toolkit.PNG)

We can connect to IoT Hub.

![IoT Hub Toolkit, No IoT Hub connected](images/Connect_To_IoTHub.PNG)

You will be asked to select subscription (you may have to log in first).

![IoT Hub Toolkit, Select subscription](images/Connect_To_IoTHub_Select_Subscription.PNG)

Next pop up will ask for IoT Hub, you will likely have just one on the list, unless you created some before.

![IoT Hub Toolkit, Select IoT Hub](images/Connect_To_IoTHub_Select_IoTHub.PNG)

That should result in successful connection and you should see your device's name on the list.

![IoT Hub Toolkit, List of devices](images/Connect_To_IoTHub_DeviceList.PNG)

It's time to send a message to a device. Right click on it and look for "Start monitoring C2D Message".

![IoT Hub Toolkit, Monitor C2D Message](images/Connect_To_IoTHub_Start_Monitoring_C2D.PNG)

Let's go back to the portal, we will send from there a message to device.

![Azure portal, Device overview](images/Connect_To_IoTHub_DeviceInfo.PNG)

Select "Message to device" tab and send some text.

![Azure portal, Send message to device](images/Connect_To_IoTHub_Send_Message.PNG)

Go back to VS Code, you should now see your message in the output window. When you right click you can stop monitoring.

![IoT Hub Toolkit, Received message](images/Connect_To_IoTHub_Stop_Monitoring.PNG)

Right click on device name and select "Generate code", you should see a pop up asking for language choice.

![IoT Hub Toolkit, Pick language](images/Connect_To_IoTHub_Generate_Code_Languages.PNG)

You should see as one option "Send device-to-cloud message". Pick it and save project on your computer.

![IoT Hub Toolkit, Pick template](images/Connect_To_IoTHub_Code_To_Send_D2C_Message.PNG)

Go back and right click on device name again, this time pick "Start monitoring D2C Message". Go now to your project and run it. Remember to stop your code after few messages, as you have 8000 limit per day for your IoT Hub.

![IoT Hub Toolkit, Send telemetry](images/Connect_To_IoTHub_Send_Telemetry.PNG)

As a result in VS Code with monitoring turned on, you should see messages sent from device.

![IoT Hub Toolkit, Received telemetry](images/Connect_To_IoTHub_Monitor_Telemetry.PNG)

And we now have working code for our device which communicates with IoT Hub.

----------------


## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/tomaszbartoszewski/IoTHub-tutorial/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/tomaszbartoszewski/IoTHub-tutorial/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
