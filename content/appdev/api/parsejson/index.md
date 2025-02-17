---
title: Parse JSON
weight: 2
---
# What is Parsing
Parsing is breaking a block of data into smaller pieces (tokens) by following a set of rules (using delimiters for example), so that this data could be processes piece by piece (managed, analysed, interpreted, transmitted, ets).

How do we parse JSON in Python. First we load a JSON file using **json.load()** method. The result is a **Python dictionary**. We can then access the fields using dictionary methods.

JSON is a lightweight data-interchange format.

To extract information from a JSON file or a JSON response, we have to parse the data.
## Parse JSON in Python
### Convert JSON to a Python Dictionary

It’s a good idea to convert JSON to a Python dictionary when you want to use the data in your code because this lets you access all of the supporting functions dictionary objects offer in Python. The next example uses **json.loads()** to convert the JSON into a Python dictionary. It then uses a few of the built in functions of the dictionary object and prints the results to the console:



We will use the following JSON in our example:

{{< highlight python >}}
{
	"orders": [ 
		{
			"size": "medium",
			"price": 15.67,
			"toppings": ["mushrooms", "pepperoni", "basil"],
			"extra_cheese": false,
			"delivery": true,
			"client": {
				"name": "Jane Doe",
				"phone": null,
				"email": "janedoe@email.com"
			}
		},
		{
			"size": "small",
			"price": 6.54,
			"toppings": null,
			"extra_cheese": true,
			"delivery": false,
			"client": {
				"name": "Foo Jones",
				"phone": "556-342-452",
				"email": null
			}
		}
	]
}
{{< /highlight >}}

Please take a moment to analyze the structure of this JSON file.

Here are some quick tips:

- Notice the data types of the values, the indentation, and the overall structure of the file.
- The value of the main key "orders" is an array of JSON objects (this array will be represented as list in Python). Each JSON object holds the data of a pizza order.
If we want to read this file in Python, we just need to read and create a dictionary with the statement:
{{< figure src="loads.png" title="" >}}

{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=31" >}}
    def jsonpractice(self):
        file = """{
	"orders": [ 
		{
			"size": "medium",
			"price": 15.67,
			"toppings": ["mushrooms", "pepperoni", "basil"],
			"extra_cheese": false,
			"delivery": true,
			"client": {
				"name": "Jane Doe",
				"phone": null,
				"email": "janedoe@email.com"
			}
		},
		{
			"size": "small",
			"price": 6.54,
			"toppings": null,
			"extra_cheese": true,
			"delivery": false,
			"client": {
				"name": "Foo Jones",
				"phone": "556-342-452",
				"email": null
			}
		}
	]
}
"""
        data = json.loads(file)
{{< /highlight >}}

**json.loads(file)** creates and returns a new Python dictionary with the key-value pairs in the JSON file.

Once we have the content of the JSON file stored in the data variable as a dictionary, we can use it to do basically anything we want.

## Examples
For example, if we write:

{{< highlight python >}}
print(len(data["orders"]))

{{< /highlight >}}
The output is **2** because the value of the main key "orders" is a list with two elements.

We can also use the keys to access their corresponding values. This is what we typically do when we work with JSON files.

For example, to access the toppings of the first order, we would write:
{{< highlight python >}}
data["orders"][0]["toppings"]

{{< /highlight >}}
- First, we select the main key "orders"
- Then, we select the first element in the list (index 0).
- Finally, we select the value that corresponds to the key "toppings"

You can see this "path" graphically in the diagram:
{{< figure src="image-101.png" title="" >}}

If we print this value, the output is:
{{< highlight python >}}
['mushrooms', 'pepperoni', 'basil']
{{< /highlight >}}


## Let's look at some live weather data


There are 1000s of APIs for use in software and web development on a variety of topics including sport, jokes, bitcoin etc. Before you can start using an API you need to first need to read the API Documentation to understand what parameters need to be used.

In this example we are using a free weather API that doesn't require an authentication key and just needs **{location}** to be replaced. 

{{< highlight python >}}
https://weatherdbi.herokuapp.com/data/weather/{location}
{{< /highlight >}}

{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=31" >}}
    def btn(self):
        #Set the location we are looking for
        location = "Adelaide"

        # GET request to web server for data in json format and add the location to the end
        response = requests.get("https://weatherdbi.herokuapp.com/data/weather/" + location)

        # print the data recieved from the server
        print(response.json())

        # create a formatted string of the Python JSON object
        text = json.dumps(response.json(), sort_keys=True, indent=4)
        print(text)
        print("---------------------------------------------------")

        # convert the JSON file into a Python dictionary to extract data
        json_data = json.loads(response.text)
        
        # print the current temperature of the location in degrees celsius
        print(json_data["currentConditions"]["temp"]["c"])
        todays_temp = json_data["currentConditions"]["temp"]["c"]
        print("Current temperature is " + str(todays_temp))
{{< /highlight >}}

- What other data can you display from the API?
- Now show it on your APP!

<iframe src="https://tmccatholiceduau-my.sharepoint.com/personal/tnykke_tmc_catholic_edu_au/_layouts/15/embed.aspx?UniqueId=c8632564-d060-535e-c769-710d0387f4fc&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="API Kivy pt2-20220310_015136.mp4"></iframe>

<iframe src="https://tmccatholiceduau-my.sharepoint.com/personal/tnykke_tmc_catholic_edu_au/_layouts/15/embed.aspx?UniqueId=96e73101-8536-5dc9-21ce-0a68fb0194a7&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create" width="640" height="360" frameborder="0" scrolling="no" allowfullscreen title="API Kivy pt3-20220310_015150.mp4"></iframe>