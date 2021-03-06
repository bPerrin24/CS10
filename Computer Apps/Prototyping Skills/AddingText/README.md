# Adding Text



---

# Ideas to included
CAUTION
- If text is too small or too big, it will not print
- This is fixed in Typing Examples from SP2

---

# Example Code (Read only in ATOM)
Specific Group of Functions: Printing Text to the Screen – Typography (Search Term)
- Note: the processing website has excellent progression of explanations with these
- Getting the typography ready: Menu/Tools/CreatFont
- Createing the varaible & declaring it: PFont() & createFont():
- createFont() is better than loadFont() which can only be used in setup
- Setting up Typography: textAlign()
- Setting up fullScreen calculations and verifying the fit or use of scalar: textWidth()
- Printing typography: textFont(), text()
  Note: textFont() includes textSize()
- More advanced features for typography exist

Function Choices
PFont [varaibleName]
createFont( "name", size) //See Processing.org/reference for other parameters
  //Must be in void setup(){}
fill( ) //
textAlign(CENTER)
textFont( variableName, size)
text( stringVariableName | intVaraible | floatVaraible, x-coord, y-coord, textBoxWidth, textBoxHeight)
fill() //return fill to previous setting or default setting

Example Script: basic text on screen
// Title Bar
fullScreen();
String title = "Cue Cards";
PFont titleFont;
titleFont = createFont ("Arial-Black", 55); //Copy spelling from CreateFont
rect (displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10); //Title Rectangle
fill (0); //Black Ink
textAlign (CENTER); //Centered in Rectangle
textFont(titleFont, 60); // Change the Size number
text(title, displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10); // Title "Cue Cards"
fill(255); //Reset to white for rest of program

Auto Sizing Algorithm: Flat
fullScreen();
String title = "Cue Cards Study Tool"; //  String must be "long enough"
PFont titleFont;
titleFont = createFont ("Arial-Black", 55); //Copy spelling from CreateFont
rect (displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10); //Title Rectangle
textFont(titleFont, 40); // Type of font needed for calculation, size needed for function
textAlign (CENTER);
textSize (displayHeight*1/10); //Needed for textWidth Calculation
float textLength = displayWidth*1/2; // Needed for Variable inside FOR Loop
for (float i=1; textWidth(title) > displayWidth*1/2; i = i - 0.01) {
  textLength = textLength*i;
  textSize (textLength);
  println("For" + textLength);
} //Resizing Algorithm for Title Bar
textSize (textLength);
fill (0); //Black Ink
text(title, displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10);
fill (255);

Auto Sizing: GUI
String title = "Cue Cards Study Tool"; //  String must be "long enough"
String endCopy = "Bottom of the Page"; //  For second example, String must be "long enough"
PFont titleFont;
float textLength = displayWidth+1; //Needs a value bigger than any rectangle
titleFont = createFont ("Arial-Black", 55); //Copy spelling from CreateFont
rect (displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10);
textFont(titleFont, 40); // Type of font needed for calculation, size needed for function
textAlign (CENTER);
// Passing needed measures to Calculator
textLength = autoSize (title, displayWidth*1/2, displayHeight*1/10);
println(textLength);
textSize (textLength);
fill (0); //Black Ink
text(title, displayWidth*1/4, 0, displayWidth*1/2, displayHeight*1/10);
fill (255);

Auto Sizing: return
float autoSize (String a, int b, int c) {
  textSize (c); // for textWidth() calc
  float textLength_local = b;
    for (float i=1; textWidth(a) > b; i = i - 0.01) {
    textLength_local = textLength_local*i;
    textSize (textLength_local);
  }

  return textLength_local;
}

---
