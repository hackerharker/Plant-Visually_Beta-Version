# Project 01

## Project Description
Native California plants have many environmental benefits. They generally consume less water as they are adapted to our summer dry climates, they also provide critical food and habitat to wildlife that have coevolved with them. Many people don't want to use native California plants in their landscapes because many aren't evergreen. I would argue that the dynamic phonological changes of native California plants and plant communities makes them more interesting than a static evergreen landscape. I see the issue as largely being that people just don't know how to design planting plans using time as dynamic and feature element. My hypothesis is that if people had a tool that would help them design planting plans using phenological visualizations that people would be more inclined to plant native California plants. To solve this problem I will be creating a phenological plant chart generator. The first version of the phenological plant chart will focus on a limited number of plants that are endemic to San Francisco. Shown below is a wireframe I created previously that illustrates generally how I would like the visualization to read. I would eventually like the colors on the bar graph to be reflective of the actual coloring of the plant foliage, bloom, or other seasonal feature.

Here is a link to a wireframe I created that illustrates a similar idea:
https://www.dropbox.com/s/tofk5ctpnz7mpgq/Screen%20Shot%202020-06-13%20at%208.15.53%20PM.png?dl=0

### MVP/PostMVP

The functionality will then be divided into two separate lists: MPV and PostMVP.  Carefully decided what is placed into your MVP as the client will expect this functionality to be implemented upon project completion.

## Functional Components

#### MVP
| Component | Priority | Estimated Time | Time Invested | Actual Time |
| --- | :---: |  :---: | :---: | :---: |
| Plant class | H | 2hr | 1hr | 3hr|
| Creation of plant objects  | H | 2hr | 1hr | 3hr|
| Chart class | H | 2hr | 1hr | 3hr|
| Plant selection menu  | M | 2hr| 1hr | 3hr |

| Total | H | 8hrs| 4hr | 12hr |

#### PostMVP
| Component | Priority | Estimated Time | Time Invested | Actual Time |
| --- | :---: |  :---: | :---: | :---: |
| More plant objects, maybe link to a database| H | 4hr | -hr | -hr|
| Printing seasonal interest as a color rather than a text field| M | 8hr | -hr | -hr|
| Formatting plant names to be on the left | L | 3hr | -hr | -hr|
| Using a graphic library to create chart | H | 8hr | -hr | -hr|

| Total | H | 23hrs| -hrs | -hrs |

## Additional Libraries
 None. 

## Code Snippet
This is the code that I am most proud of, it is an instance method in the class Plant. It loops through the months in a plant object and returns the seasonal interest. In the test case seasonal interest is always a flower and corresponding flower color. This piece of code delivers a key componenent of this project. In the Post MVP I will try to move this instance function from the Plant class to the Chart class so I don't have to define the 'months' tuple in two places. Then the Plant class will only be used to creat Plant objects and print the Plant object names.

```python

    def print_interest(self):  
        interest_string = " "
        for month in self.months:
            if month in self.interest_for_month:
                interest_string = interest_string + self.interest_for_month[month] + "-"
```

## Issues and Resolutions


#### PLANT OBJECTS CAN'T HAVE THE SAME NAME AS THE PLANT OBJECT NAME
**ERROR**:  In starting this project, I kept trying to name the Plant object the name of the plant:
"""PYTHON
Erigeron glaucus = Plant({'JAN':'LAV','FEB':'LAV','MAR':'LAV', 'APR':'LAV', 'MAY':'LAV', 'JUN':'LAV', 'JUL':'LAV', 'AUG':'LAV'})
"""

**RESOLUTION**: It took me some time to realize that I had to assign a new variable to each plant that wasn't it's name so that the name could be entered as an argument and initiated with self.name.

"""PYTHON
plant_2 = Plant("Erigeron glaucus",{'JAN':'LAV','FEB':'LAV','MAR':'LAV', 'APR':'LAV', 'MAY':'LAV', 'JUN':'LAV', 'JUL':'LAV', 'AUG':'LAV'})
"""

#### REMBERING TO REFERENCE THE SELF IN AN INSTANCE METHOD OF A CLASS
**ERROR**:  In trying to print chart of plant_list, got error message 'plant_list' is not defined. I had the same issue with printing the month list. I got the error 'months' is not defined.                       
**RESOLUTION**: In the class Chart's "print chart" instance method I had "for plant in plant_list:" rather than "for plant in self.plant_list:". I was able to resolve it by prefacing plant_list with self. Similarly, I had to correct "months" to self.months. This is a mistake I made repeatedly inside classes.

#### REMBERING TO USE INSTANCE METHODS FOR CLASS OBJECT
**ERROR**: I tried to print the plants in my_plants using print(my_plants) and was given the location that the plant object was stored but did not get a list of plant names.
"""
print(all_plants)
[<__main__.Plant object at 0x114ddcdf0>, <__main__.Plant object at 0x114ddce80>, <__main__.Plant object at 0x114ddce50>, <__main__.Plant object at 0x114ddcfa0>]

"""
**RESOLUTION**: Remembering that for instance methods in a class I have to reference plant.name
"""PYTHON
for plant in all_plants:
    print(plant.name)
    """

#### VERTICAL OUTPUTS & HORIZONTAL CHART
**ERROR**:  In printing the plant interest by month it prints vertically. Same with the months in the year, when printed it prints each month in sucession vertically. This didn't work with my chart concept.                        
**RESOLUTION** Making the output into a string so that it reads horizontally. This was done in a similar way as the pallindrome homework.

"""PYTHON
        for month in self.months:
            month_list = month_list + " " + month
            
          or
          
        for month in self.months:
            if month in self.interest_for_month:
                interest_string = interest_string + self.interest_for_month[month] + "-"
                
            else:
                interest_string = interest_string + "----"    
                
                """
                
 #### PRINTING A LIST WHERE ONLY ONE ITEM IN THE LIST IS PRINTED EVEN IF I AM LOOPING
**ERROR**:  In printing the list of months or lists of plants I had an error multiple times where only the first item in the list was printed.              
**RESOLUTION** This was usually a problem with my indentation.

This version is wrong, it only prints out the first item on the list due to indents:
"""PYTHON
            else:
                interest_string = interest_string + "----"
                    print(interest_string + self.name)     

"""


This version prints out all items on the looping list:
"""PYTHON
            else:
                interest_string = interest_string + "----"
        print(interest_string + self.name)     

"""

#### PUTTING PLANT NAMES ON THE LEFT SIDE OF THE CHART DIDN'T WORK
**ERROR**:  In putting the plant names on the right side of the list the seasonal interest and the months didn't line up correctly because of the varying length of the plant names.                    
**RESOLUTION**: I moved the plant names to the right side of the chart. Visually it's not ideal and I'd like to find a better resolution.


