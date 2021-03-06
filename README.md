# Bapabackup
## Final for CS390N IoT Rubric


### Originality
We wanted to make something that would make real life more efficient, but without adding another doohickey into your daily life. Thus, we decided to integreate the IoT into something you (or at least we) use every day: your backpack. 


### Technical difficulties
#### The RFID module

Where to begin! The RFID module we use is consistently seen in online tutorials alongside a breakout board cleverly designed to convert its impractically tiny XBee pins to a breadboard friendly size, and obfuscating the actual inner workings of the module. This made it hard for a RFID module non-expert to dig into the data sheet and ground the correct pin, and compels the consumer to shell out another twenty for the breakout. Since we were on a budget, parsing that gem took a good half week.

The next challenge was to implement an interrupt-based activation scheme for reading data to the board, as the module was integrated into software using the polling method. We luckily found a pin that could do exactly what we needed to activate a digital interrupt by spending some quality time with the data sheet.

#### The accelerometer

The method of sensing motion that we originally envisioned involved deriving acceleration readings twice at set interrupt intervals (the interrupts being something that remained in our final version).  These data would be muxed (multiplexed) to a single analog (ADC) pin, and saved as approximations of dx, dy, and dz (as this was a three-dimensional accelerometer). These dx, dy, and dz readings would be added to a vector called displacement, and each element in said vector would be squared, summed, and rooted to find the overall displacement. Unfortunately, consumer-grade accelerometers simply arent precise enough for such things. Instead we used some mathematical trickery to get an approximation of net movement, and found that to work just as well.


### Design approach
Our design approach was simple: integrate the technology seamlessly into the user's everyday life so as not to force a change in habits or routine. Just as before, the user puts their things in a backpack, and walks out the door. Only, as soon as the backpack is swung onto the user's back, and the backpack notices something missing, it sends a notification to your phone. Otherwise, your day proceeds as normal. If the IOT is truly the future, we believe its uses will evolve in this direction, with minimal doohickeys and daily-routine interruptions.


### Accuracy
To determine the weather, we query yahoo, and check the results agains a defined set of possible weather patterns. This lets the board know whether to include an umbrella in its list of expected items. Our fallibility in this respect lies in the hands of the weather services of a multinational tech giant.

To determine the other things needed for the day, we use google calendar. Accuracy here actually depends on the user's use of his or her calendar.

RFID checking has several safeguards in its parsing method.
The accelerometer measures pure acceleration. We anticipate an earthquake providing a false positive there.

NOTE: the mega API we use for this is Temboo, our login for which has since expired. 

### Information delivery
Using Blynk's notification widget, we send a personalized notification telling the user they forgot something, and the unique identifier of the thing they forgot.


### Testing and results
We made sure to make individual test sketches for each element of the project that was worked on at a time, and we have them here in our repository. Please feel free to poke around. Once we had tweaked each element to our liking, we added it methodically to Final.ino, adding its initialization method to setup() to minimize clutter in setup(), and initializing its relevant variables inside its own delineated section of the code. We found that this method led to highly flexible development.


### Showcase Presentation Quality
You have reached the end of the README! Thank you for attending our showcase. It was a pleasure sharing our project with you, and we hope you walk away today as excited as we are about the Internet of Things.



