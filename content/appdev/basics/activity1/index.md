---
title: Activity 1
weight: 4
---
## Setting up The Python Script
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import kivy
from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.gridlayout import GridLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
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

<iframe src="https://tmccatholiceduau-my.sharepoint.com/personal/tnykke_tmc_catholic_edu_au/_layouts/15/embed.aspx?UniqueId=f16fe7ca-8daa-5e69-3df4-9679cfda1b6e&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="Kivy Activity 1-20220228_061123.mp4"></iframe>
# Activity 1
1. Add a Surname **Label** and **TextInput** so when the user presses the submit button the surname is also included.
2. Add a **Label** that welcomes the user when submit is pressed
{{< figure src="Screenshot 2022-02-28 164502.png" title="" >}}

<iframe src="https://tmccatholiceduau-my.sharepoint.com/personal/tnykke_tmc_catholic_edu_au/_layouts/15/embed.aspx?UniqueId=cc99a762-5e0d-56aa-f92c-65ba990a2cb5&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="Kivy Activity 1 sol-20220228_062609.mp4"></iframe>





