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


i even made the entire pcb but then i realised i wired everything wrong , here is that pcb i designed- 


<img width="1201" height="484" alt="Screenshot From 2026-08-11 15-16-31" src="https://github.com/user-attachments/assets/22fe2f1f-d38f-440b-9a8e-9264d3fd5c0e" />


okay i copied over the components and lets redesign the schematic . 


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/65f0f0a9-f38f-4756-8b45-430fd11c0a87" />


my goal is to make it the same as the layout 
because at first when i saw 61 keys i thought i could wire them in a 5x12 manner but turns out i need to do it how the layout is


in the top most layer there are 14 switches so we will wire 14 switches in the first column

in this way 

<img width="956" height="132" alt="image" src="https://github.com/user-attachments/assets/8cd12f83-b42d-46ef-bf2c-eaea9c9466c4" />

now see not each switchis of the same size , so how would we know what size of swtich we would need to use? 
well in the keyboard layout editor you click the switch and down below it shows the width , which is the size of the switch you need to use

this is for the backspace key 

<img width="518" height="473" alt="image" src="https://github.com/user-attachments/assets/1af22aab-e462-47d9-8c4a-5761d64e6beb" />


and then you go into your footprint library and pick the correct size . im using cherry mx switches so my footprints may vary 

we want to pick the pcb one footprint as it has space for supports 
which we would need for the space bar and other big keys 

<img width="763" height="334" alt="image" src="https://github.com/user-attachments/assets/829d3572-aa05-45b6-b9af-ee99356e871f" />

and we will repeat this method for each key 


in the second column we again have 14 keys but this time the switch sizes are different, 2 keys exactly 

<img width="827" height="62" alt="image" src="https://github.com/user-attachments/assets/6cfeab84-eefc-423c-9dca-2f95659712d9" />


and for our 3rd row we have 13 switches with the tab and enter key differenly sized

<img width="827" height="62" alt="image" src="https://github.com/user-attachments/assets/a37f81c2-b483-4c3d-b257-c6f6ccf3290c" />

and in our 4th row we only have 12 keys 

<img width="827" height="62" alt="image" src="https://github.com/user-attachments/assets/de026434-bda4-4292-a294-ace5c8d24277" />


my bad it turns out i miscounted the switches in my schematic in the top layer , it is indeed 14 but i put only 13 switches 

here is how it should look like 


<img width="1281" height="227" alt="image" src="https://github.com/user-attachments/assets/02cb6404-0109-46f6-9819-5a1ecb9e05a1" />


in our 5th and last row we have only 8 switches so here is how the schematic looks like- 



<img width="914" height="474" alt="image" src="https://github.com/user-attachments/assets/4e735ccb-20ab-46b2-a314-e79510e86ffc" />



here is the proper schematic with the rows and columns respectively 

<img width="914" height="474" alt="image" src="https://github.com/user-attachments/assets/83e035ab-615a-4454-b76a-01442e3abd7d" />

okay so because you copy the rows and paste them to save time , you would have to annotate which renames the switches so dont freak out like me 

<img width="1047" height="558" alt="image" src="https://github.com/user-attachments/assets/504fed3d-cfef-433f-a679-cc8f17b6051f" />

here are the footprints ive assigned everything

<img width="601" height="838" alt="image" src="https://github.com/user-attachments/assets/2d3a3e1f-2d1c-493f-b8dc-3b338253f178" />


<img width="601" height="838" alt="image" src="https://github.com/user-attachments/assets/fefb5129-6530-472c-b071-690e7e15ea12" />



now lets load everything onto pcb editor and start designing our pcb 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a4294e7a-6af3-4675-b461-f38ec734f94a" />

oh and i decided to not use the rotary encoder , ill use it for a different project

and here is how i wired the pi pico 

<img width="354" height="437" alt="image" src="https://github.com/user-attachments/assets/6ed40036-c423-45cd-acac-9df696772237" />


okay so here is what im doing 
im taking each diode and putting it on the other side of the pcb 

<img width="611" height="529" alt="image" src="https://github.com/user-attachments/assets/a3514fc0-37b4-4787-a2e2-30934af46943" />

and then im removing the refrences and values because all diodes are the same in my pcb


