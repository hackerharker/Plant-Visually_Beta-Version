# Plant Visually Beta Version
This is the beta version of the Plant Visually phenological chart generator. The final project can be found [here](https://github.com/hackerharker/Plant-Visually).

![Plant Visually Beta](plant_visually_beta.gif)

## Summary
The first version of the phenological plant chart includes four plants that the user is prompted to add to a list by responding 'yes' or 'no'. A chart is generated using text to display a three letter abbreviation of the plant flower color in the month that the plant is blooming.

## Functional Components

#### Currently Implemented
| Component | Priority | 
| --- | :---: | 
| Plant class | H |
| Creation of plant objects  | H | 
| Chart class | H | 
| Plant selection menu  | M | 

#### Future Work
| Component | Priority |
| --- | :---: |  
| More plant objects, maybe link to a database| H | 
| Printing seasonal interest as a color rather than a text field| M | 
| Using a graphic library to create chart | H | 

## Code Snippet
This is the code that I am most proud of, it is an instance method in the class Plant. It loops through the months in a plant object and returns the seasonal interest. In the test case seasonal interest is always a flower and corresponding flower color. This piece of code delivers a key componenent of this project. 

```python
    def print_interest(self):  
        interest_string = " "
        for month in self.months:
            if month in self.interest_for_month:
                interest_string = interest_string + self.interest_for_month[month] + "-"
```
