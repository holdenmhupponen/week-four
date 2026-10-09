- opened "linlithgow_spatial.ipynb"
- ran first cell, the initialization - worked without error
- ran second cell, with geometry and comments - worked without error:
> **geometry  context  EARLIEST_DATE**  \
0  LINESTRING Z (0.757 15.466 0, 0.757 15.531 0, ...      331           1400   
1  LINESTRING Z (1.037 15.512 0, 1.036 15.525 0, ...      331           1400   
2      LINESTRING Z (1.046 15.503 0, 1.558 15.466 0)      331           1400   
3  LINESTRING Z (4.289 14.642 0, 4.289 14.754 0, ...      146           1400   
4  LINESTRING Z (4.622 14.604 0, 4.621 14.624 0, ...      146           1400

> **LATEST_DATE   AGE_AT_DEATH  BURIAL_POSITION     SEX GRAVE_SHAPE**  \
0         1560  ADULT (26-45)  SUPINE EXTENDED  FEMALE     ROUNDED   
1         1560  ADULT (26-45)  SUPINE EXTENDED  FEMALE     ROUNDED   
2         1560  ADULT (26-45)  SUPINE EXTENDED  FEMALE     ROUNDED   
3         1560  ADULT (26-45)  SUPINE EXTENDED  FEMALE     ROUNDED   
4         1560  ADULT (26-45)  SUPINE EXTENDED  FEMALE     ROUNDED
 
> **COMMENTS**  
  0  NORTH OF HIGH ALTAR  
  1  NORTH OF HIGH ALTAR  
  2  NORTH OF HIGH ALTAR  
  3  NORTH OF HIGH ALTAR  
  4  NORTH OF HIGH ALTAR

- ran third cell, with the plotted graph - worked without error:
 <img width="1241" height="554" alt="image" src="https://github.com/user-attachments/assets/c4d37ffc-812d-410e-a184-5eaf86c8aa4e" />
 
- changed variable "cmap=" from "Accent" to "afmhot" - worked without error:
   <img width="1241" height="554" alt="image" src="https://github.com/user-attachments/assets/9f1fe8c1-57e6-4195-a666-b740c73e9ace" />

- ran fourth cell, with the "tidy" formatted dataset - worked without error
  - couldn't find a way to replicate it inside this log

- ran fifth and sixth cells, with only the burials before 1400 - worked without error
  - ran seventh and eight cells, with the same result as the one above, but with only the burials earlier than 1500 - worked without error

- ran ninth cell, with the burials sorted by sex - worked without error
  - ran tenth cell, which also sorted burials by sex but without the "UNK" entries - worked without error
 
- ran eleventh cell, which used a 'groupby' command to sort burials by "AGE-AT-DEATH" - worked without error
  - ran twelfth cell, which further examined the specific age group of "adult_burials" from the eleventh cell's output - worked without error
  - ran thirteenth cell, which did the same as the twelfth but for "infant_burials" - worked without error
 
# pause and consider:
- i created a markdown cell as directed and wrote the following answer:
> "In both the adult and infant burials, the "ROUNDED" graves are the most common, the "NOT DEFINITIVE" graves are the second-most common, and the "ANGULAR" graves are the least common. Despite the shared ranking, the ratios differ. The adult burials contain more definitive grave shapes -- meaning a value that is not "NOT DEFINITIVE" -- and the infant burials contain less definitive grave shapes."

- ran fourteenth cell, which plotted the adults and infants and colour by grave shape - worked without error:
  <img width="1228" height="508" alt="image" src="https://github.com/user-attachments/assets/1c1ad3ed-4beb-4d3a-9750-1f6fbcb50662" />
  - conclusion: it seems that the greater the age at death correlates to being more likely to have a definitive shape.

- ran fifteenth, sixteenth and seventeenth cells, which saved the pre-1400 and pre-1500 selections as "pre1400" and "pre1500" variables, and called them into formatted lists - worked without error

- ran eighteenth cell, which used a "total_bounds" command to find the "bounding box" of the pre1400 variable - worked without error:
  - "array([-0.44993622,  2.56715295, 41.31863521, 16.15619505]\)"
 
- ran nineteenth cell, which called the total_bounds of the pre1500 variable - worked without error:
  - "array([ 4.08110118,  0.15121173, 41.04023533, 15.10604186]\)"
  - asked to consider why this result was not identical to the last one, despite "pre-1500" technically including "pre-1400":
    - i believe it's because the coordinates only represent the "bounding box," or a boundary, meaning that its dimensions would only be affected by the farthest values in whichever direction; so the pre1500 variable, containing all of pre1400 and more, might expand the boundary if those additions existed outside the boundary set by pre1400
  - ran twentieth cell, which plotted a specific burial, the "195" 'context' of the pre1500 variable - worked without error:
    <img width="566" height="249" alt="image" src="https://github.com/user-attachments/assets/f7658e58-0338-476c-b8d8-48f6721bb49f" />
  - ran twenty-first cell, which plotted the 189 context of the pre1500 variable - worked without error:
    <img width="566" height="212" alt="image" src="https://github.com/user-attachments/assets/67380656-e642-47e3-9314-05357a019db0" />
  - ran twenty-second cell, which plotted both the 189 and 195 burials - worked without error:
    <img width="566" height="212" alt="image" src="https://github.com/user-attachments/assets/28aa728a-00e3-49fd-b67b-710ec0066ed6" />
    - i see that the orientation of 195 is slanted while 189 is horizontal; that 195 has a fish-like shape while 189 is an imperfect rectangle.
   
# infant burial contexts
- ran twenty-third cell, which defined "linlithgow_infants" as only the set of values in "linlithgow_burials" that contained the INFANT value in AGE_AT_DEATH and no others - worked without error
  - ran twenty-fourth cell, which used the linlithgow_infants variable to plot all the infant burials - worked without error:
    <img width="1228" height="442" alt="image" src="https://github.com/user-attachments/assets/64b7ba5e-b351-495c-ad46-fb345b4df548" />

- ran twenty-fifth cell, which defined "linlithgow_infants_close" as a 'buffer' command that makes each burial line 0.5m thick - worked without error:
    <img width="1228" height="442" alt="image" src="https://github.com/user-attachments/assets/8bc4664b-f62d-4c54-ae6a-4b2eff103007" />
    
- ran twenty-sixth cell, which defined "burials_near_infants" as the intersection of all burials to the "linlithgow_infants_close", then plotted it - worked without error:
    <img width="1228" height="484" alt="image" src="https://github.com/user-attachments/assets/24841492-0f41-4736-8a94-4d9fd965c2e8" />
  - i can conclude that most of the burials were made within 0.5m of infant burials: this can be seen in the blue colour that shows the intersection; there are only a few burials that are not coloured in blue.







 
