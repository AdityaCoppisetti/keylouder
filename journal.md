


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

# THE SCHEMATIC

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

# THE PCB 

now lets load everything onto pcb editor and start designing our pcb 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a4294e7a-6af3-4675-b461-f38ec734f94a" />

oh and i decided to not use the rotary encoder , ill use it for a different project

and here is how i wired the pi pico 

<img width="354" height="437" alt="image" src="https://github.com/user-attachments/assets/6ed40036-c423-45cd-acac-9df696772237" />


okay so here is what im doing 
im taking each diode and putting it on the other side of the pcb 

<img width="611" height="529" alt="image" src="https://github.com/user-attachments/assets/a3514fc0-37b4-4787-a2e2-30934af46943" />

and then im removing the refrences and values because all diodes are the same in my pcb


oh and btw the entire last colum has different sized switches

<img width="831" height="82" alt="image" src="https://github.com/user-attachments/assets/a8fc8197-1c25-401b-9c2a-48aedb44cbca" />


oh and apparently it took me this long to realise i didnt put the size for the space bar and didnt mention it in the schematic 

<img width="1135" height="606" alt="image" src="https://github.com/user-attachments/assets/22eece76-bd65-4906-9beb-3a6ca090377a" />

here it is now 

<img width="599" height="245" alt="image" src="https://github.com/user-attachments/assets/3b943cdd-dc56-45f5-b03d-a29e81d95d82" />

okay so at first i didnt account for stabilizers which you would need so that the keycaps stay flat on the keyboard. 
so i went to add stabilizers in my schematic but i couldnt find the symbol so i just took a capacitor and gave it that footprint. 
also the footprint for that i got from a different package which apparently has 3d models of everything so im going to switch the footprint of each key to one from that library. 

the reason i used capacitors is because i already mapped out the keys in the pcb and if i would have used switches instead of capacitors it wouldve had me annotate the pcb again which would mess everything up and i would have to start all over. 

secondly when choosing stabilizers you ignore whats after the decimal point in the size 

<img width="232" height="529" alt="image" src="https://github.com/user-attachments/assets/c9eee3c8-83dd-429f-b216-581e6bcfb9c5" />

if the size is 2.25 , you pick 2, etc. 


okay so i completed the pcb routing completely 

<img width="996" height="417" alt="image" src="https://github.com/user-attachments/assets/8a44b723-245b-49ee-9e96-ba2e7171a625" />

now lets make the case 

here is how the pcb looks like in 3d view
and before we do that we have to define the pcb parameters using the edgecuts layer and drawing a rectangle. 

<img width="1267" height="506" alt="image" src="https://github.com/user-attachments/assets/2937f420-e144-47aa-a4d2-18e2ec70da5f" />

also then we are going to define a positive and ground plane 

and i went ahead and added VBUS and GND power symbols to the schematic 

<img width="589" height="693" alt="image" src="https://github.com/user-attachments/assets/3c7be3b4-61d0-49da-b2b4-9a62dd4abb4c" />

after adding the VBUS fill zone here is how it looks like 

<img width="1206" height="477" alt="image" src="https://github.com/user-attachments/assets/ec89c57c-23bf-47e8-a123-c624ce7544d4" />

and then then GND one 

<img width="1206" height="477" alt="image" src="https://github.com/user-attachments/assets/39ac85d1-0d0e-4d4f-8335-7b4f7cc05606" />

end result- 

<img width="1206" height="477" alt="image" src="https://github.com/user-attachments/assets/8eb34d15-d2d2-446a-bb2c-a86d767e4fb0" />


look how much better the pcb looks 

<img width="1258" height="447" alt="image" src="https://github.com/user-attachments/assets/faf12b91-1ca4-4259-a345-d74f51bc6f0b" />

and here is a lil 360 as always 





https://github.com/user-attachments/assets/9dbf6d89-2aa4-4465-9659-0ed4b1decdad


before we get started on the case i dont like the empty space below the pi pico so im thinking of adding a led matrix to it and have fun animations on it 



okay so i was reading this tutorial https://www.hackster.io/diyguyChris/diy-customized-8x8-led-matrix-tutorial-max7219-meets-arduin-06a3a7

<img width="632" height="475" alt="image" src="https://github.com/user-attachments/assets/ae3703c9-bb37-41a0-afa3-929e9134d7ed" />


and the person had built a tiny module for their arduino and it got me thinking what if i built my own module instead of letting the components be on the keyboard pcb.

now that open alot of doors because then i would be able to hotswappable modules like one with a led matrix and then one with a tiny oled display and one with a rotary encoder.
this is exciting!!


# THE LED MATRIX MODULE 

Using the schematic provided in the tutorial ill reacreate that schematic in kicad , lets make a new project file within our project and start building the schematic 

<img width="1010" height="733" alt="Screenshot From 2026-08-12 16-22-33" src="https://github.com/user-attachments/assets/29d182f7-8e8a-4a1f-8cda-5a3db70055b9" />

okay i wired the ic , 

<img width="483" height="532" alt="image" src="https://github.com/user-attachments/assets/392d6f50-3fad-4b7a-bda7-3240c45f42c0" />



now we need to make the led matrix and wire that to it 

<img width="684" height="802" alt="image" src="https://github.com/user-attachments/assets/44d651bf-b875-435d-8884-b0118cbd7a45" />

made it now we need to wire it to the ic 

Okay i did it and here is how it looks like-

<img width="867" height="588" alt="image" src="https://github.com/user-attachments/assets/8754f17f-284f-45cc-a35d-7db0bf5e86f4" />

we now need to make the pinout 

<img width="531" height="301" alt="image" src="https://github.com/user-attachments/assets/94126aef-caa8-4542-8d5b-17c938a3c623" />

okay i made a mistake the net labels werent the same because in the matrix the r is lowercase and in the ic wiring the net label was upercase 



# THE FOOTPRINTS 
For the leds this is the footprint im using- 

<img width="1152" height="618" alt="image" src="https://github.com/user-attachments/assets/377a8d6d-5193-4567-ae31-c71cb76e677a" />

LED_SMD:LED_0201_0603Metric

for the ic im using this 

<img width="1152" height="618" alt="image" src="https://github.com/user-attachments/assets/c005750d-1d3e-4dde-9059-4490f01a1eb7" />


for the resistor 

<img width="1152" height="618" alt="image" src="https://github.com/user-attachments/assets/6666e625-6409-4be0-aba5-7d0c4a1e9ccc" />


and then the resisitor

<img width="1152" height="618" alt="image" src="https://github.com/user-attachments/assets/742dab01-8518-4686-8465-41ade46bb6ea" />

# THE LED MATRIX PCB

but before we do that i need to see how much space we have below the pi pico in the keyboard pcb.

looks like we have plenty space


<img width="619" height="486" alt="image" src="https://github.com/user-attachments/assets/669e8bed-b9bd-492a-949e-31a9e943177c" />

i finally got done routing everything oh my god its so time taking 

<img width="360" height="504" alt="image" src="https://github.com/user-attachments/assets/9705d652-390f-4cbe-bdea-ed0d01ea9fe0" />


okay now lets design the case. 

## THE CASE

ookay so i opened kicad pcb editor and exported my file in . step 

<img width="580" height="580" alt="Screenshot From 2026-08-12 14-28-17" src="https://github.com/user-attachments/assets/16ba6a4b-5f32-4f83-9006-ed45675ff71b" />


<img width="371" height="195" alt="image" src="https://github.com/user-attachments/assets/14336fed-b38e-4c66-8f2f-7bad73718ad5" />


now lets open onshape and import our pcb boards. 

<img width="253" height="324" alt="image" src="https://github.com/user-attachments/assets/704d1ce6-c3ee-4b45-886b-2fdc10d23bd9" />

combine it into the same part studio.

i do this because its so much easier to make the case then and then i make sure that nothing is mapped out wrong plus at the same time i create project mockups to use as the preview picture 

the pcb looks so amazing in onshape 

<img width="1267" height="516" alt="image" src="https://github.com/user-attachments/assets/c998e491-4186-418f-8ba9-121ed6a506cf" />


oh my god i totally forgot to add connecting pins for the led matrix bahahahah

okay so i added connection in the main keyboard schematic and let now also put it on the pcb 


<img width="924" height="591" alt="image" src="https://github.com/user-attachments/assets/3b5eb31e-fdde-4d84-8708-649820e55f88" />

before we do that lets clean up our schematic 

i personally like to keep everything neat so this part is upto you 

<img width="1225" height="485" alt="image" src="https://github.com/user-attachments/assets/d5546962-7d5f-42f0-95ca-2eaecb55f45b" />


okay so i updated the main pcb here is how it looks like now

<img width="1225" height="485" alt="image" src="https://github.com/user-attachments/assets/94860a12-1071-495b-85f9-1af96a534854" />

oh and i totally forgot i need to add holes to put screw thru so that i can mount it onto the case 

now our pcb has holes so i can put screws thru them and we will be using 4mm heat inserts in the case keep in mind. you can choose any heat inserts you want 

<img width="1060" height="397" alt="image" src="https://github.com/user-attachments/assets/d35263cb-b2e3-4613-b1c2-ac1caed7a3db" />

here is a lil 360 



https://github.com/user-attachments/assets/b619c04f-7e00-4aa9-93fa-9f7086f12ad5



now lets import this again into onshape and lets stard designing the case 


okay so im making this structure in the case which is totally optional but im making this so that the pcb is sturdy and doesnt bend from the weight of my hand 

<img width="1031" height="461" alt="image" src="https://github.com/user-attachments/assets/fa62bb02-9d0f-477a-9d5e-12785db4d2af" />

<img width="1461" height="564" alt="image" src="https://github.com/user-attachments/assets/083834e8-4d3c-4e11-9e5a-1329ce41b2ad" />


oh and the holes in the corner are so i can put heat inserts and then screw down the keyboard 


okay so i made the case and i added a little hole for the c type port. im going to use a male to female c type wire and then route it beneath the pcb and into the hole 

<img width="965" height="668" alt="image" src="https://github.com/user-attachments/assets/b84ae705-a019-4a37-b79c-1ab5fca6fd14" />


here is how the pcb looks like inside the case 

<img width="1233" height="491" alt="image" src="https://github.com/user-attachments/assets/df646430-4e4a-48fe-85d8-d036310de067" />


the little led matrix sits so flush and perfectly on the board its crazy 



https://github.com/user-attachments/assets/e525fbdb-a991-4f65-9065-cdec64515798


okay so i found this key and keycap cad file and im downloading it to use for my mockup 

<img width="896" height="638" alt="image" src="https://github.com/user-attachments/assets/5e0b0659-ea1b-47a5-a1a5-336e17014183" />


<img width="896" height="638" alt="image" src="https://github.com/user-attachments/assets/01dc9eef-1bbb-437d-a384-bee735f94168" />


now im going to add everything together in assembly and design mockups 


<img width="555" height="582" alt="image" src="https://github.com/user-attachments/assets/7a7dac03-cfc3-42c1-9b36-ed579e2eca91" />


my laptop is struggling really hard to load all of this bahahahha




<img width="1351" height="523" alt="image" src="https://github.com/user-attachments/assets/951fb9ba-0d07-4488-976f-6e0e918eeac3" />


my laptop is getting so hot 

<img width="1001" height="727" alt="image" src="https://github.com/user-attachments/assets/c8beeaaa-5e35-4907-b91d-3eee8dc08e6d" />


<img width="1001" height="727" alt="image" src="https://github.com/user-attachments/assets/d7b523ac-6c87-4714-90ae-7c61231e4d37" />


<img width="1214" height="507" alt="image" src="https://github.com/user-attachments/assets/9a70a866-c4c8-4873-ba35-b59cbe8acbc7" />


i fear my laptop may fucking blast 

<img width="1447" height="655" alt="image" src="https://github.com/user-attachments/assets/0b222438-ae3d-45f2-bd65-e60352f79e4a" />

okay so i genuinly think something will blow up because of how laggy and hot my laptop is getting 

<img width="1447" height="655" alt="image" src="https://github.com/user-attachments/assets/3492018e-18de-44a3-abb4-5e786d28569d" />

i want to make more modules , simple ones now , like a oled display module and then a rotary encoder module and 
 i want to add this sliding module aswell


now lets make the rotary encode module! 


 
 <img width="1447" height="655" alt="image" src="https://github.com/user-attachments/assets/a41d99cf-8326-4688-a18e-6c7d0ffcd62e" />

 but i might make it for a different keyboard or project 



# ROTARY ENCODER MODULE!!!!!!!!!!!!!!!!


okay so ill be using this rotary encoder

<img width="1265" height="596" alt="image" src="https://github.com/user-attachments/assets/9cb6baa2-1af0-44fa-9d2b-0c8e65be3bc4" />

okay so you can do this with a perfboard aswell. 

ill be desoldering the pins on the rotary encoder and then soldering the rotary encoder onto my module pcb because the pins we have set for gnd and vcc is different that the ones needed for the rotary encoder

OKAY SO BAHAHAHAHAHHAH THIS IS HOW BIG THE SCHEMATIC IS , ITS THE BIGGEST SCHEMATIC IVE EVER MADE

<img width="696" height="393" alt="image" src="https://github.com/user-attachments/assets/92b5b4e0-7d4c-4faf-9cec-d78439461a2e" />

okay so what its basically doing is that it takes the pin on the main keyboard pcb and then makes it suitable for the rotary encoder 

<img width="411" height="707" alt="image" src="https://github.com/user-attachments/assets/27c77088-ded6-4f59-9b4d-b71fe7f541c4" />



and then these are the footprints 

<img width="688" height="109" alt="image" src="https://github.com/user-attachments/assets/d9191a5b-39a4-416a-a527-56badbc4cc71" />


this is how simple the module really is 

<img width="782" height="552" alt="image" src="https://github.com/user-attachments/assets/f46cc12c-81a9-4d30-abb2-41b000280cb0" />


the most difficult pcb today oh my my 


<img width="784" height="598" alt="image" src="https://github.com/user-attachments/assets/da94f669-59cc-4546-be0b-d7c5f761bc03" />


there is literally no point in making fill zones but i think it gives the board a nice look 

<img width="784" height="598" alt="image" src="https://github.com/user-attachments/assets/ae518b9c-2f19-464a-bea8-820e6d64e266" />


<img width="784" height="598" alt="image" src="https://github.com/user-attachments/assets/52e91e3e-bbb2-471b-bc1b-71bf8f5e5bde" />

and obviously ill import it into onshape and make a mockup 

apparently i cant do that because as soon as i open the asembly now it just freezes my laptop and im worried that my hackatime lapse footage will corrupt :(


# August 13th 10.30 am

yesterday night after i got done working i was thinking about what sort of modules i should make and i asked my friend and he recommended me to make a tamogotchi digital pet which would be so cool 

so let me figure out how to make that after i make just the plain oled display module

now i know i shouldnt let the pi pico do all of that so i will use my tiny xiao microcontroller 
that i have or im going to use the esp32 module the one that doesnt have bluetooth or wifi.

all of this seems really really cool and exciting! 

# the display 

okay so after browsing robu.in
i found this really cool round display module 

<img width="1500" height="1044" alt="image" src="https://github.com/user-attachments/assets/6cfd2bb1-b3ac-4364-9c49-245cbdf1e455" />


it is the GC9A01 7-pin, 240×240, 1.28-inch round TFT module, SKU R123209

it seems really simple to let me see if instead putting this display module ontop of my swappable module i can just make this into the same pcb 


and here is the given datasheet measurements of the display 

<img width="642" height="491" alt="image" src="https://github.com/user-attachments/assets/918efcb5-cc16-49b8-af4e-1b42b7220779" />


# the micrcontroller 

ill be using the ESP32-C3-WROOM-02U

<img width="209" height="190" alt="image" src="https://github.com/user-attachments/assets/90b4f536-6a09-4c43-8ec8-9394dee00178" />

its the same as the other esp32 module that i use besides the fact that it doesnt have inbuilt wifi and bluetooth antenna 

ive built multiple esp32 modules before so this shouldnt be a problem 

lets open kicad and get started 

okay so because there isnt a proper datasheet on how the schematic of the display is , ill just be using the display module itself rather than having a tft screen soldered down on my pcb 

# the buttons 

<img width="1029" height="509" alt="image" src="https://github.com/user-attachments/assets/3d444860-a885-4876-8b2f-9e8ff2bc05f7" />

i will be using these tactile switches cause i really really like them 

## the schematic for tamagotchi module 

<img width="932" height="609" alt="image" src="https://github.com/user-attachments/assets/00f0df70-a2bd-4ccc-b5a9-43c633748d9e" />


i have put the main parts now lets design the tiny esp 32 board

wired just the main module 

<img width="458" height="539" alt="image" src="https://github.com/user-attachments/assets/c6304478-602c-428e-ab13-4eb872edcbda" />

wired the power and data input 

<img width="649" height="544" alt="image" src="https://github.com/user-attachments/assets/25e7ae07-be0e-4523-a5bb-e98d1b495bad" />

okay here is everything 

<img width="498" height="651" alt="image" src="https://github.com/user-attachments/assets/842899d7-6bb1-4624-8ff7-76f13c24f20c" />

now lets add display out and buttons 

here is the complete schematic with the buttons and display input

this is the footprint of the pcb 

<img width="714" height="740" alt="image" src="https://github.com/user-attachments/assets/eb9a475d-3cf3-496b-b102-6a654ed0b28d" />

now lets get started on the pcb 




<img width="593" height="775" alt="image" src="https://github.com/user-attachments/assets/e6734e90-6f85-424a-8dc1-91feca4f7a21" />


 now lets make the pcb 

 ## the tamagotchi module pcb

  the 12mm switches were too big so i switched it to 6mm


  i forgot to add the input pins from the keyboard pcb 

  
<img width="714" height="740" alt="image" src="https://github.com/user-attachments/assets/f37acb26-1f04-46a7-8265-eb101846d398" />

the 3rd 4th and 5th pin do absolutely nothing 


i wired it so that the buttons are only using one pin because i didnt have any pins remaining for the display 

<img width="727" height="764" alt="image" src="https://github.com/user-attachments/assets/9fd44a98-819d-4e0d-979f-65cab4944c15" />

beacuse

<img width="616" height="349" alt="image" src="https://github.com/user-attachments/assets/05326742-c7c8-4c5f-af92-b5e1bbc10e27" />

each button will now have a unique value and thus we can use them with the same gpio pin 


okay so the pcb wiring is done i got so overstimulated i had to calm my mind down 

<img width="396" height="598" alt="image" src="https://github.com/user-attachments/assets/238cf8df-46ed-4d5e-9342-8c65d8dcfbd0" />


here is how the pcb looks like in 3d view 

<img width="396" height="598" alt="image" src="https://github.com/user-attachments/assets/a1a93006-7002-4c76-a65f-62caf026dae2" />

and 

<img width="396" height="598" alt="image" src="https://github.com/user-attachments/assets/9cada9d7-e29b-4242-b6d0-fbeb863a8d3f" />


and obviously here is a little 360


https://github.com/user-attachments/assets/ace1704f-5848-4185-81a5-730ddb79b4bb


now lets see if i can try to make a mockup 
and also i want to build just one more module thats just a screen

also i want to rebuild the case and make it really really cool

i want to give the case a skeleton look 


i have something like this in mind 

<img width="868" height="938" alt="image" src="https://github.com/user-attachments/assets/bfc948b3-b49b-4f0b-af93-b233c14aa58d" />

 i dont want to mess my previous case up so im creating a different onshape document entirely and exporting the pcb again


 i made holes in the pcb so i could screw it in and mount it , i however think that the holes ive made are too big so i might have to design a specific washer 





 <img width="1092" height="436" alt="Screenshot From 2026-08-13 17-39-40" src="https://github.com/user-attachments/assets/c86d15b8-6df3-4d08-9d1b-740cde968069" />



i have made the outline of the case now lets remove parts using extrude feature and make it look cool asf 



<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/2856ae9e-a513-4789-9d96-b0f4c74b7a78" />


this is what im thinking about also this looks so bad but ykw its something that represents me 


<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/64d2a733-0895-44fa-b9d1-ba3419137045" />


okay so i did another side and i pray to go this looks better in life 

<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/29a959dc-8df6-4c56-825b-4b6f97447066" />

aaaandddd another side done , wont be doing it on one side and then ill do the bottom layer 

<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/d6ecc956-b65e-4801-b035-9765e6260c75" />



just made the bottom layer sketch

<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/ac388237-0d1f-4162-8062-c281852d3493" />


i mean i guess it'll work 


<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/57b1154d-1389-45aa-bf37-39ada4478ac6" />



made the bottom layer sketch in the skeleton case manner lets see if its any good 

<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/2c5dacaf-8203-4c33-9c7f-7c1f32837a47" />


now lets see if the tamagotchi module will fit 



the tamagotchi module will definitely fit for sure 

<img width="1383" height="775" alt="image" src="https://github.com/user-attachments/assets/fc281b5e-e2e0-433f-b4ea-345d96ee598c" />


this is such a cool project 

<img width="1491" height="594" alt="image" src="https://github.com/user-attachments/assets/03c37096-dce5-4d47-afc1-d8f905f038ad" />


well its a first so im happy with it 

<img width="1425" height="590" alt="image" src="https://github.com/user-attachments/assets/0fcd6192-a1a3-48a3-9f6b-da7dc309ac59" />

but let me still once try redesigning the bottom layer 


made a much much MUCH better sketch 

<img width="1239" height="603" alt="image" src="https://github.com/user-attachments/assets/369c6065-5930-49d2-bf82-d889746d06d9" />



i made a couple of changes and now here is the final product 

<img width="1239" height="603" alt="image" src="https://github.com/user-attachments/assets/d263ee78-4e91-4be4-9556-a06015758120" />



made just one more tiny hole 

<img width="1364" height="594" alt="image" src="https://github.com/user-attachments/assets/48d16038-bf82-42bc-a6a8-ee21cf612189" />


i also want to add images to my silkscreen but ill do it at the very last 


## august 15th 

today ill be doing a couple of things. 
i honestly thought i was almost done because i had made the case and everything. 
it turns out there was still alot i need to make- 

1) i want to add backlight to the keyboard however i dont want to do anything too fancy
2) i want to make the tamagotchi module better by using a xiao rp2040 and not using a esp32 however i will still be making that
3) i need to make the middle plate for the keyboard apparently
4) i want to add images on my silkscreen

but my question is how will there be backlight if im using a middle plate?

i mapped everything out and here is how the sketch of the mid plate looks like 

<img width="1288" height="488" alt="image" src="https://github.com/user-attachments/assets/4ecf9dbe-f965-47a7-8e00-0363ac5c250d" />


and im glad i did that because i realised that i didnt made the case mounting holes tall so the pcb would have been mounted really really low 
when i extrude that sketch i want it to be really really slim 


here is how it looks like when extruded

<img width="1400" height="531" alt="image" src="https://github.com/user-attachments/assets/c05f5a14-5489-429c-b8b9-bc18a4e68f86" />

i went ahead and made the moutning holes in the case smaller 

<img width="1641" height="632" alt="image" src="https://github.com/user-attachments/assets/a0f7334f-1a65-48c0-a882-8c732b7b3f60" />

and then i made the stand-offs and it lowk looks okayish i mean its not the best

<img width="1392" height="673" alt="image" src="https://github.com/user-attachments/assets/e9f6e8a5-a058-4700-be7b-815d1470ed1a" />

in my previous case design i made a little cutout for the usb wire but i now realised i wouldnt need that since the pi pico is on pinheaders and thus it'll have some height yk and so i wouldnt have any problem with connecting it to a wire , however i dont think the pi pico comes in type c


<img width="1392" height="673" alt="image" src="https://github.com/user-attachments/assets/71d1a1ec-f87a-4b75-92ac-2964d2d37c42" />


# now lets make the tamagotchi module better 

im going to be using the xiao rp2040 because i already have that and you can use a perfboard for this aswell

this is the symbol and footprint

<img width="1146" height="597" alt="image" src="https://github.com/user-attachments/assets/b342fc55-c8cf-4160-8a09-5a36d214dd05" />


<img width="773" height="600" alt="image" src="https://github.com/user-attachments/assets/54387ffc-fa04-4f43-8034-6c83a32e966e" />

also i think im going to redesign the case oh lord 

i went ahead and designed the schematic

<img width="1058" height="645" alt="image" src="https://github.com/user-attachments/assets/6bbd1120-9b87-4c92-a051-cc323c75b94f" />

and then here are the footprints


<img width="751" height="208" alt="image" src="https://github.com/user-attachments/assets/d107fc68-0922-48ac-8f38-646d050a15a8" />


## now lets make the pcb 


look at how little components we need in this and how simpler it is 

i copied and pasted the pcb measurements and the pin header positions

it seems like i did the wiring perfectly 

the pcb is super simple 

i made it so that the xiao rp2040 is on the other side of the board 

<img width="855" height="782" alt="image" src="https://github.com/user-attachments/assets/681b6f83-be20-49a8-88dd-57c5001df7b7" />


these board are so simple that ill be making them using a perf board , only the simple ones tho 

ive also added a bvuzzer and i totally forgot to update my pcb and add the pins for that and i hadnt connected the power input for the xiao 


and here is how it looks like after its updated and fully wired 

<img width="855" height="782" alt="image" src="https://github.com/user-attachments/assets/1c3013b2-6087-4748-9ccf-2e6e00becc82" />

now lets export it into .step and make mockups 


okay so here is how that looks like 

<img width="769" height="729" alt="image" src="https://github.com/user-attachments/assets/cc5890da-54ad-40ef-bde2-fe0ad99ac616" />

oh yeah and i changed the middle plate colour to blue because grey was really weird


let redesign the case for the 3rd fucking time now


also before i do that , it seems like i made the mounting holes in the pcb way too big 
and also lets add images to silkscreen


here is the updated pcb with the correct mounting holes 


<img width="1340" height="489" alt="image" src="https://github.com/user-attachments/assets/6c939aac-463b-4785-8b1b-7b6070c42db7" />


here it is in 3d viewer

<img width="1219" height="484" alt="image" src="https://github.com/user-attachments/assets/0230152d-8725-4200-b698-0afb98b59f77" />


and the back 

<img width="1219" height="484" alt="image" src="https://github.com/user-attachments/assets/7888f797-4cf0-43c3-8687-77e617bd4f03" />


and obviously here is the lil 360 



https://github.com/user-attachments/assets/513a91aa-45da-4924-ba17-3ebb43d4cd46


here is the new case design sketch also i realised this is the fourth version of the case 


<img width="1281" height="598" alt="image" src="https://github.com/user-attachments/assets/8e1d92ad-d981-4a1a-9068-90d0d47d0e02" />

fingers crossed i hope this looks good 

<img width="1281" height="598" alt="image" src="https://github.com/user-attachments/assets/466427e1-c649-4c19-8a29-dd41cb368c7e" />


okay moment of truth now i made the extruding layer 

<img width="1281" height="598" alt="image" src="https://github.com/user-attachments/assets/fae05e13-f18e-48da-b79c-764765008b0c" />


honestly if we werent removing , this would look so cool if extruded that way 

<img width="1250" height="738" alt="image" src="https://github.com/user-attachments/assets/92ce37c2-7341-4dde-9092-14db370c0cfa" />


apparently i had a lot of errors the way i had plotted the shaped to be removed and finally after so many trials 

<img width="1250" height="738" alt="image" src="https://github.com/user-attachments/assets/9dc03add-ad2a-42d2-b304-505ac821ff5b" />


okay it doesnt look that good but i have an idea , i have an old acrylic glass panel lying around and i think im going to put between the pcb and the case



now lets get started on the other sides
