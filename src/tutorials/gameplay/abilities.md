## Overview

An ability is anything that the player can do themselves. 

Anytime that a player can do something more than just jump and crouch, that should be added to a CORE™ project as an ability. Abilities are how a creator can add functions that a player can activate, and these abilities can be anything. 

An ability could be to sprint, a dance emote, the opening of a hidden menu; an ability can be anything that ought to happen on a button press or at a certain moment, repeatedly.

!!! info
    Comparing with Unreal and other game engines, an ability is basically a fancier keyboard input. "Fancier" because it has events built-in that can be set at each phase of execution.

![Dodge Roll](src/docs/img/EditorManual/Abilities/dodgeRoll.GIF)

### What is an Ability?

In CORE, an ability is an object that holds information about how to function. You can set how long the ability lasts for, how long until the ability can be used a second time, and all sorts of other properties.

While there are ways to utilize all these properties, for your first dive into abilities, we're just going to touch on the very basics.

Abilities can either be assigned to players at the start of a game, or when they equip a special item.

## Tutorial

Adding a simple ability to a game is only a couple of steps. We'll go over how to activate an animation on a button press, with no coding necessary!

We're going to make a piece of equipment that the player can pick up, and when they do, they will gain a new ability.

In this tutorial, we are going to make a super simple dodge roll.

### Getting Started with Equipment

1. With CORE open to a project, click on **Object** in the top menu bar and down on the list click "Create Equipment".  
   
     This will add an **Equipment** object to your project Hierarchy. Equipment comes with a `PickupTrigger` that allows players to equip the object when the player touches it.

     Doing this will already let you pick up the equipment when playing the game and walking through it--but it's hard to pick up something you can't see!

2. To make this a more useful power-up object, let's add a model to it that players can see.  
    
     You can really choose whatever you would like, but in my case I am going to use a classic gem.  

       1. In the **Asset Manifest**, search for "diamond" and drag the `Gem - Diamond 6-Sided Polished` into your Project Hierarchy.  

         Feel free to change the material, or make the model suit your own game more. To learn more about how to make cool art & models in CORE, read our [Art Reference Guide](src/docs/art/art_reference/) or try a [Tutorial](src/docs/art/modeling_basics/). 

       2. Drag it onto the Equipment object and it will become a child of the equipment object. It will prompt you to make the Gem Networked, and select Yes to this.  
         For better organization, right click the Gem object and select `New Group Containing This`, and name it "Art".

       3. In the **Properties** window, uncheck the "Collidable" box of the art folder. This way the gem won't mess with your camera when it's attached to the player.  

     Now that we've created a visible object that can be picked up, it needs to do something!

4. Up in the **Object** menu, click "Create Ability" to add an ability object to your project Hierarchy.  

     1. Click on the Ability object and drag it onto the Equipment object to make it a child of the ability object. Now when the player picks up the equipment, they will automatically gain the ability!

6. The Ability object starts with default settings in the Properties window. To make our own dodgeroll, we only need to change two things.  

     1. With the Ability Object selected, navigate to the Properties window and change the **Key Binding** property to "Ability Feet".  

        The Key Binding is which button will activate the ability. In this case, Ability Feet is the shift key on keyboards.

     2. Still in the Properties window and right beneath the Key Binding, change the **Animation** property to `unarmed_roll`.  

### CORE Component: Ability Display

A crucial part of a video game is the feedback it gives--players need to know that they're using an ability.

While you can make a User Interface *(often abbreviated to UI)* element yourself, there is a pre-made template on **Community Content** that we can use to very quickly set up simple UI for our new ability!

When the ability is in the Cooldown phase, it will darken the ability button and show the seconds remaining until the ability is usable again.

![Ability Display](/src/img/EditorManual/Abilities/abilityDisplay.GIF)

To get this to work correctly with the ability we made above, there are only a few steps steps:

1. In Community Content, search for the **CORE_Component_AbilityDisplay** template by jishnugirish, and add this to your project by clicking the blue plus icon.  
  ![Ability Control](/src/img/EditorManual/Abilities/CORE_Component_Ability.PNG)

2. Navigate through your **Project Content** to the **Imported Content** section, and drag the **green** component called **CORE_Component_AbilityBindingDisplay** into your Hierarchy.  

3. If you now click this template from in the hierarchy, the **Properties** tab will show a few custom properties that we need to change to set up the ability display.
  ![Ability Control](/src/img/EditorManual/Abilities/AbilityButtonProperties.PNG)  
      1. Change the **Binding** property from `ability_primary` to `ability_feet`. 

      2. Change the **Text** field to `LS`, to stand for Left Shift. 

      3. Uncheck the **HideName** property, so that "Dodge" will display over the button.  

      What is really the key here is the Binding property--this connects whatever ability is currently bound to that binding to the Ability Display.

4. To **change the icon that displays** from a fork & knife to something more relevant for our ability, navigate through the AbilityBindingDisplay folders in the Hierarchy to the two Icon objects. Change the **Image** property on these to whatever you would like!  
 ![Hierarchy](/src/img/EditorManual/Abilities/ComponentHierarchy.PNG)  
     I chose the **Icon Stamina** for this case. 

Now the UI element will update automatically once the ability is cast.

Congrats on creating your first ability! You are well on your way to making anything you can imagine a reality.

### Networking for Multiplayer Games

Abilities themselves work in multiplayer games perfectly without any extra programming effort. If you made your own ablity UI icon and did not use the Community Content template above, the UI will not update properly in multiplayer games. For the UI to update as the ability happens, the UI relating to the player's abilities must be placed in a Client Context folder. 

This has already been done for us in the Community Content template, so no action is needed!

!!! info "Client Context"
    Generally speaking, all UI related to the player should be in a Client Context folder. For more info on how networking works, visit the [related Networking page].

## Altering Properties the Easy Way: The Ability Object

Abilities can get more complex, and often you may want to tweak the values in an ability quickly without having to open up scripts. 

To create a more advanced ability system and read more about Ability Objects, read our [next tutorial on abilities](/tutorials/gameplay/complex_abilities/).

## Examples

*FAA_GameMode* includes functioning abilities.  
*Spellshock* includes advanced abilities using ability objects. 