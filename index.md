# Translating Basic Excel to Python: Part 1
By Scott A. Adams

In a previous post I covered how to perform basic spreadsheet-based analytics in SQL. This article shows how to perform the same analytics in Python. Before we jump in, though, you may be asking, "why learn Python?" While there are many reasons that I could enumerate here, there are three particular reasons I want to highlight. First, Python skills are in-demand, so learning Python can enhance your marketability as a data professional. Second, as a general programming language Python has many applications in various domains, from data analytics to machine learning to web application development. Third, as an open-source programming language there are numerous functions and libraries of functions to perform a wide array of tasks. Furthermore, if a given task you want to perform is not addressed by all the functions that others have written, it is possible to write your own function.

Before moving further, note that the examples covered in this article run Python code in Google Collaboratory ("Colab" for short). If you want some more details on using Colab, see this prior post, "Getting Started with Python in Google Colab." In addition, all materials for the exercises covered below are accessible here on GitHub. Now, let's dig in to see how to perform basic analytics in Python.

## Importing Necessary Libraries
Python is a modular programming language, meaning that most pieces of functionality need to be manually imported. For example, in Excel the function to compute the mean of a set of numbers is available for use when the software opens, without requiring any additional special actions. When running Python, computing the mean requires the import of a function that can return the mean from an input set of numbers. Why do this? This practice is resource efficient. Instead of loading a large set of functions and using only a handful that are necessary for the job at hand, only load the required functions. The image below details the import of a library, where you can think of a "library" in Python as collection of previously written code that performs various tasks.


Let's break this import statement down. The import command instructs Python to execute the function named import. pandas is the name of the library being imported, which in this case is a popular library for data manipulation and analyses named pandas. The use of as pd after pandas assigns the alias pd to pandas, which is a technical way of saying that pandas is renamed to pd in this Python session after this line of code is executed.

## Load Your Data
The pandas library has a useful function named read_excel, which reads data from an Excel spreadsheet file into a pandas DataFrame, which is simple a data storage format comprised of rows and columns, much like a spreadsheet. Documentation on read_excel function, and all other functions in the pandas library, can be found on the pandas webpage.

Image of the read_excel page
Below is an annotated image of the code that reads an Excel file, containing the New York City Airbnb Open Data from Kaggle, into a DataFrame.

No alt text provided for this image
This line of code begins with df, which is a variable name. In this context, think of a variable as container for something. Consider the code and output below, for example.

```
>>> x = 2
>>> print(x)
2
```

I created a variable named x which holds the number 2. When I use the print function to output the contents of the variable x the returned output is not x but 2, because with x = 2 I instructed Python to recognize that x references a piece of data, which in this case is the number 2.

In the same way df = instructs Python to assign something to the variable named df. Note that I could have used any name for the variable I wanted, but I used df because this is a common convention to refer to a DataFrame, particularly in tutorials. Now, to the right of the assignment operator (i.e., the equal sign) is that something being assigned to df. Recall that libraries can contain functions, so pd.read_excel instructs Python to use the read_excel function from the pandas library. The read_excel function is contained in the pandas library, so the library name comes first, followed by the function. You can think of the period between the library name and function as a way of indicating that the read_excel function belongs to the pandas library. At this point it is worth emphasizing that had I not aliased pandas as pd I would have needed to write

df = pandas.read_excel("https://raw.githubusercontent.com/sadams26/excel_to_python/main/data/AB_NYC_2019.xlsx")
Thus, aliasing pandas saved me from writing four additional letters (though I am writing more words here to explain, but such is life).

The parentheses immediately following a function contain parameters, which, to keep things simple, can be thought as additional instructions on what the function will output. Notice in the read_excel documentation that the first parameter listed is io.

No alt text provided for this image
Here, think of io simply as a placeholder for the Excel file of interest. Importantly, io has to be a string, which means a piece of text. How do you specify that something should be treated as text in Python? Put the text in-between quotation marks.

Alright, now that the data is loaded let's look at how to perform some basic analytic operations.

View Your Data
So, you want to see the data in the df DataFrame? Just write df in a code cell and run.

No alt text provided for this image
A few things to note. First, the leftmost column in the output shown above is not a column but an index, which can be thought of as a row number in the case of a DataFrame. But why is the first row labeled "0"? Python is zero-indexed, meaning that the enumeration of an index starts with 0, not 1. Second, the index goes from 0, 1, 2, 3, 4, to ... to 48,890. What did I do wrong?! In this case, nothing is wrong. The output is simply truncated.

If you are coming from Excel or similar spreadsheet software this may be unsetting as you are used to seeing all the data within a spreadsheet. While this may be comforting to see all of the data, it is the application of analytic functions to the data that produces meaningful insights, not the eye-balling of the entire dataset. With that said, it can be useful to glance at a snapshot of the data to make sure everything loaded correctly. Here, I recommend using the head function from pandas, which, by default, will return the first five rows of a DataFrame.

No alt text provided for this image
Want to see more than five rows? Input the desired number of rows in the parentheses following head.

Wrapping Up
Now you have the knowledge and tools that will allow you to read data from an Excel file into Python. Tune in next week for part 2 of this topic, where I will cover filtering, aggregate functions, and pivot tables with pandas. Thanks for reading!
