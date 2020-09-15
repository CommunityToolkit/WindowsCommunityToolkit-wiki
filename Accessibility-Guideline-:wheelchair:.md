We'll follow this guideline to ensure the basic accessibility features for each control.

## Color & High Contrast Themes
* Controls must support the 4 high contrast themes by default on Windows, in addition to changing the theme while the app is running.
* Controls must have a contrast ratio of at least 4.5:1 between the text (and images with text) and the background behind it.

## Keyboard
* Controls must support keyboard navigation (tabs and arrow keys), the tab order must be the same as the UI and non-interactive elements mustn't be focusable.
* Composite elements must ensure proper inner navigation among the contained elements
* Clickable UI elements must be invokable with the keyboard (The trigger keys are enter and space).
* Focusable elements must have a visual focus indicator. It's usually a rectangle shape around the control's normal bounding rectangle.

## Narrator
* Controls must support the narrator.

## Naming conventions
* We are following the coding guidelines of .NET Core Foundational libraries.
