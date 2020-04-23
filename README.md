# Pygame Widgets

A helper module for common widgets that may be required in developing applications with Pygame.
It supports fully customisable buttons, collections of buttons and textboxes.

## Prerequisites

* [Python 3](https://www.python.org/downloads)

## Installation

Ensure that Python 3 and pip are installed and added the PATH.

```python -m pip install pygame-widgets```

Open a Python console and run the following command.

```import pygame_widgets```

If you receive no error the installation was successful.

## Usage

### Button

A customisable button

#### Example Usage
```
import pygame
from pygame_widgets import Button

pygame.init()
win = pygame.display.set_mode((600, 600))

button = Button(
            win, 100, 100, 300, 150, text='Hello',
            fontSize=50, margin=20,
            inactiveColour=(255, 0, 0),
            pressedColour=(0, 255, 0), radius=20,
            onClick=lambda: print('Click')
         )

run = True
while run:
    events = pygame.event.get()
    for event in events:
        if event.type == pygame.QUIT:
            pygame.quit()
            run = False
            quit()

    win.fill((255, 255, 255))

    button.listen(events)
    button.draw()

    pygame.display.update()
```

This button will be placed at (100, 100) with a width of 300 and a height of 150,
display the text 'Hello' with font size 50, leaving a margin of 20 and a radius of 20.
When clicked, the button will change colour from red to green and 'Click' will be printed to the console.

#### Mandatory Parameters

_Note: Mandatory parameters must be supplied in order._

| Parameter | Description | Type |
| :---: | --- | :---: |
| win | Surface to be displayed on. | pygame.Surface |
| x | X-coordinate of top left. | int |
| y | Y-coordinate of top left. | int |
| width | Width of button in pixels. | int |
| height | Height of button in pixels. | int |

#### Optional Parameters
| Parameter | Description | Type | Default |
| :---: | --- | :---: | :---: |
| inactiveColour | Default colour when not pressed or hovered over. | (int, int, int) | (150, 150, 150) |
| pressedColour | Colour when pressed. | (int, int, int) | (100, 100, 100) |
| hoverColour | Colour when hovered over. | (int, int, int) | (125, 125, 125) |
| shadowDistance | Distance to projected shadow. Set to 0 if no shadow desired. | int | 0 |
| shadowColour | Colour of shadow | (int, int, int) | (210, 210, 180) |
| onClick | Function to be called when clicked. | function | None |
| onClickParams | Parameters to be fed into onClick function. | (*any) | () |
| onRelease | Function to be called when released. | function | None |
| onReleaseParams | Parameters to be fed into onRelease function. | (*any) | () |
| textColour | Colour of text. | (int, int, int) | (0, 0, 0) |
| fontSize | Size of text. | int | 20 |
| text | String to be displayed. | str | '' |
| font | Font of text. | pygame.font.Font | Calibri |
| textHAlign | Horizontal alignment of text. Can be 'centre', 'left' or 'right'. | str | 'centre' |
| textVAlign | Vertical alignment of text. Can be 'centre', 'top' or 'bottom'. | str | 'centre' |
| margin | Minimum distance between text / image and edge. | int | 20 |
| image | Image to be displayed. | pygame.Surface | None |
| imageHAlign | Horizontal alignment of image. Can be 'centre', 'left' or 'right'. | str | 'centre' |
| imageVAlign | Vertical alignment of image. Can be 'centre', 'top' or 'bottom'. | str | 'centre' |
| radius | Border radius. Set to half of width for circular button. Set to 0 for no radius. | int | 0 |


### ButtonArray

A collection of similar buttons

#### Example Usage

```
import pygame
from pygame_widgets import ButtonArray

pygame.init()
win = pygame.display.set_mode((600, 600))

buttonArray = ButtonArray(win, 50, 50, 500, 500, (2, 2),
                          border=100, texts=('1', '2', '3', '4')
                         )

run = True
while run:
    events = pygame.event.get()
    for event in events:
        if event.type == pygame.QUIT:
            pygame.quit()
            run = False
            quit()

    win.fill((255, 255, 255))

    buttonArray.listen(events)
    buttonArray.draw()

    pygame.display.update()
```

#### Mandatory Parameters

_Note: Mandatory parameters must be supplied in order._

| Parameter | Description | Type |
| :---: | --- | :---: |
| win | Surface to be displayed on. | pygame.Surface |
| x | X-coordinate of top left. | int |
| y | Y-coordinate of top left. | int |
| width | Width of button in pixels. | int |
| height | Height of button in pixels. | int |
| shape | Number of columns and rows of buttons (columns, rows). | (int, int) |

#### Optional Parameters

_Note: Optional parameters of ButtonArray are similar to those of Button._

| Parameter | Description | Type | Default |
| :---: | --- | :---: | :---: |
| colour | Background colour of array. | (int, int, int) | (210, 210, 180) |
| border | Thickness between buttons and between the edges of array and buttons. | int | 10 |
| topBorder | Thickness between top of array and top of button. Overrides border. | int | border |
| bottomBorder | Thickness between bottom of array and bottom of button. Overrides border. | int | border |
| leftBorder | Thickness between left of array and left of button. Overrides border. | int | border |
| rightBorder | Thickness between right of array and right of button. Overrides border. | int | border |
| separationThickness | Thickness between buttons. Overrides border. | int | border |

### TextBox

A box for text input or display

#### Example Usage

```
import pygame
from pygame_widgets import TextBox

def output():
    # Get text in the textbox
    print(textbox.getText())

pygame.init()
win = pygame.display.set_mode((1000, 600))

textbox = TextBox(win, 100, 100, 800, 80, fontSize=50,
                  borderColour=(255, 0, 0), textColour=(0, 200, 0),
                  onSubmit=output, radius=10, borderThickness=5)

run = True
while run:
    events = pygame.event.get()
    for event in events:
        if event.type == pygame.QUIT:
            pygame.quit()
            run = False
            quit()

    win.fill((255, 255, 255))

    textbox.listen(events)
    textbox.draw()

    pygame.display.update()
```

#### Mandatory Parameters

_Note: Mandatory parameters must be supplied in order._

| Parameter | Description | Type |
| :---: | --- | :---: |
| win | Surface to be displayed on. | pygame.Surface |
| x | X-coordinate of top left. | int |
| y | Y-coordinate of top left. | int |
| width | Width of button in pixels. | int |
| height | Height of button in pixels. | int |

#### Optional Parameters

| Parameter | Description | Type | Default |
| :---: | --- | :---: | :---: |
| colour | Background colour, | (int, int, int) | (220, 220, 220) |
| textColour | Colour of text. | (int, int, int) | (0, 0, 0) |
| borderColour | Colour of border. | (int, int, int) | (0, 0, 0) |
| borderThickness | Thickness of border. | int | 3 |
| radius | Border radius. Set to 0 for no radius. | int | 0 |
| onSubmit | Function to be called when return / enter is pressed. | function | None |
| onSubmitParams | Parameters to be fed into onSubmit function. | (*any) | () |
| placeholderText | Text to be displayed when empty. | str | '' |
| fontSize | Size of text. | int | 20 |
| font | Font of text. | pygame.font.Font | Calibri