i started this project back in june? 
i cant really rememeber but then i abandoned this project because i couldnt understand the keyboard layout and the pcb mapping. 
well some youtube tutorials later i figured how to make the layout. 

i went to this website to figure out the keyboard layout what is basically does is it shows you the keyboard layout and the size of the keys. 

https://editor.keyboard-tools.xyz/

you see something like this when you open the website , you can use whichever website you find comfortable, for me its this website. 

<img width="985" height="541" alt="image" src="https://github.com/user-attachments/assets/f0030e5b-1774-4a45-a374-ed45e4d6faea" />


there are pre-existing presets , you can even build you custom presets,
then you can choose whichever keyboard layout you want.

<img width="229" height="461" alt="image" src="https://github.com/user-attachments/assets/f3a36a96-427d-4b93-ab15-55ed7f65f79d" />


i decided to make a 60% keyboard since i already have a 60% keyboard and i love its layout

it looks like this- 

<img width="922" height="354" alt="image" src="https://github.com/user-attachments/assets/9be80bff-60c3-4cc5-8ce1-9b6fc5800d17" />

and then you open kicad and then open schematic editor and take a switch and diode. 
why? 
because there are 61 switches and we are using the raspberry pico which clearly doesnt have the pins required to wire each switch seperately. 

so here is what we are going to do , we are going to make a matrix of switches in this manner- 

<img width="544" height="570" alt="image" src="https://github.com/user-attachments/assets/374533a0-93b1-4c07-90c9-d5f161ac981f" />

and then we will wire them up in rows and columns like this- 

<img width="732" height="647" alt="image" src="https://github.com/user-attachments/assets/c223e3b9-763e-4174-a840-e76f57095981" />

3 rows and 3 columns, this is basic maths combination. 

okay ill quickly explain the wiring diagram. 

and the diodes are there so no swtiches falsly seem to be pressed , i.e ghost clicking

so basically each switch is now unique since it has a unique value . 
for example switch one is wired so that when pressed it'll be - row1 and column 1. and for switch 2 it'll be row2 and column1 

okay so using this idea we make the full schematic for the needed 61 keys ( because its 60%) 

okay so this schematic wiring is a bit wrong, i need to fix it but it explains the logic. 

<img width="1064" height="754" alt="image" src="https://github.com/user-attachments/assets/c4787111-9b93-459c-b8eb-5fede3bb2fbe" />

see the rows and columns 

we will call this schematic version 1 
<img width="458" height="214" alt="image" src="https://github.com/user-attachments/assets/86442e19-e2d9-4920-8d1b-a7a5a5fa50ca" />

just for understanding the logic 
