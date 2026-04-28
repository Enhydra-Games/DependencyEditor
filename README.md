# Documentation
Documentation for the Dependency Editor Unity Plugin

## Table of Contents
- [Editor Window](#editor-window)
  - [Left Panel](#left-panel)
  - [Middle Panel](#middle-panel)
  - [Right Panel](#right-panel) 
- [Examples](#examples)
- [Code](#code)
  - [Attributes](#attributes)
    - [ShowInDependencyEditor](#showindependencyeditor)
    - [HideFromDependencyFilter](#hidefromdependencyfilter)
    - [HideFromDependencyCreate](#hidefromdependencycreate)

## Editor Window
<img width="1603" height="588" alt="grafik" src="https://github.com/user-attachments/assets/4832846c-09e4-4468-8eac-e27cbeb5ea46" />

To open the Dependency Editor go to ``Tools -> Dependency Editor``

### Left Panel 
<img width="404" height="284" alt="grafik" src="https://github.com/user-attachments/assets/0c216b27-6bb2-44f9-999c-3498bc1c217d" />

Allows the creation, deletion and selection of dependencies.\
The currently selected object is marked with a green text.\
All dependencies that lead up to the currently selected object are colored blue.\
All objects that depend on the currently selected object are colored orange.\

Whenever you create a new object through this interface, it will automatically be placed in ``Assets/Dependencies``.\
Alternatively you can create the objects by hand and place them wherever you want.\

When selecting a class in the ``Type`` dropdown, only objects that **inherit** from this type are shown in the list below. **NOT** just exactly that type. This can be useful if you manage multiple types of dependencies in your game, e.g. Skill Trees, Unlockables, Weapon Trees, etc

### Middle Panel
<img width="608" height="366" alt="grafik" src="https://github.com/user-attachments/assets/850442b3-1fcb-445f-bc73-31fc7ff6f6bd" />

Allows modifying the selected object.
The ``Type-Specific Fields`` get automatically populated based on the fields of the class used that have the [ShowInDependencyEditor](#showindependencyeditor) Attribute.

Objects can be drag and dropped from the Left Panel onto the green fields in the Dependencies and Dependents sections to easily add them to the dependency tree.

### Right Panel
<img width="544" height="456" alt="grafik" src="https://github.com/user-attachments/assets/aafad247-dd2a-4fdc-88fc-bef2da62d40c" />

Shows the current dependency network.\
The currently selected object is colored green.\
All dependencies that lead up to the currently selected object are colored blue.\
All objects that depend on the currently selected object are colored orange.\
If an object appears multiple times in a dependency network all instances after the first are greyed out/faded and marked with a return symbol. This is to avoid redundancy as this also stops subtrees from showing multiple times.\
All nodes in the dependency network can be clicked to immediately select the clicked object.


## Examples
Three example dependency classes and instances can be found in the "Samples" folder. REMOVE them before actually starting to use the plugin, otherwise the editor window will be automatically filled with them.


## Code
All dependency objects are ScriptableObjects inheriting from the ``DependencyBase`` abstract class.\
The custom classes do not have any restrictions besides needing to inherit from ``DependencyBase``


### Attributes
Attributes allow the customization of what is, and what is not shown in the Editor Window.

#### ShowInDependencyEditor
Target: ``Variable``\
Placing the ``ShowInDependencyEditor`` on a variable exposes the variable to the Editor Window. This means that it is shown in the Middle Panel of the Editor Window and can be freely edited there.
<img width="608" height="363" alt="grafik" src="https://github.com/user-attachments/assets/20994319-d13f-4bd1-a86f-8adebc45e815" />


#### HideFromDependencyFilter
Target: ``Class``\
Placing the ``HideFromDependencyFilter`` on a class hides it from the ``Type`` dropdown filter in the Left Panel.\
Can be used if you have a base class (e.g. ``Weapon``) and then subclasses (e.g. ``Staff`` ``Sword``). You can add the attribute on all the sub classes to only have the possibility to filter by the base class and avoid cluttering the dropdown.


#### HideFromDependencyCreate
Target: ``Class``\
Placing the ``HideFromDependencyCreate`` on a class hides it from the ``Type to Create`` dropdown in the Left Panel.
Can be used if you have a base class (e.g. ``Weapon``) and then subclasses (e.g. ``Staff`` ``Sword``). You can add the attribute on the base class to not allow creation of base class objects through the editor window.



