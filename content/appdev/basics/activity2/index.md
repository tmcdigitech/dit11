---
title: Activity 2
weight: 4
---
# Create a simple calculator



## Setting up The Python Script
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import kivy
from kivy.app import App
from kivy.uix.widget import Widget
from kivy.properties import ObjectProperty


class MyGrid(Widget):
    pass


class MyApp(App):
    def build(self):
        return MyGrid()


if __name__ == "__main__":
    MyApp().run()

{{< /highlight >}}



## Creating a .kv File
### Separated our logic from our styling and elements
There are a few conventions we need to follow when creating a .kv file.

Naming: The name of your .kv file must follow the rules below in order for python/kivy to be able to see and load the file.
1. It must be all lowercase
2. It must match with the name of your main class. (The one that has the build method)
3. If the name of your main class ends in "app" (lowercase or uppercase) you must not include "app" in your file name.

File Location: The file must be in the same directory as your python script.

File Extension: The file must be saved as type *All Files and end with .kv

For example:

My main classes name is MyApp. Therefore I will name my file my.kv.
{{< highlight python >}}
<MyGrid>:
    
    GridLayout:
        cols:1
        size: root.width, root.height

        GridLayout:
            cols:2
            Label:
                text: "Name: "

            TextInput:
                multinline:False

        Button:
            text:"Submit"
            on_press: root.btn()
        
{{< /highlight >}}

## Are you ready? 
{{< hint info >}}
Using your skills and knowledge from Activity 1 start a new Kivy project to create your calculator.  **You will need to setup the GUI to look like the following.**
{{< /hint >}}

{{< figure src="Screenshot 2022-03-07 155754.png" title="" >}}

### A Simple calculator in Python
We will start by generating a random string of 12 characters. To do that we will use the function random.choice() that returns a random character from a sequence.

### We will do the following:

1. Create code for the button that will add the two numbers together and display the answer as a string. Remember to convert the two numbers to an integer first.
2. Use a **Try** to make sure numbers only are entered.
3. Use a horizontal Box Layout to add subtraction, multiplication and divisions buttons to the app.
4. Add code for each new button


{{< figure src="Screenshot 2022-03-07 155754a.png" title="" >}}

<iframe src="https://tmccatholiceduau-my.sharepoint.com/personal/tnykke_tmc_catholic_edu_au/_layouts/15/embed.aspx?UniqueId=521d9994-807e-5f49-a9eb-18a041d92d4b&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="Kivy Activity 2-20220309_123103.mp4"></iframe>








