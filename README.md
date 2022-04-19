# SpaceX
## Swift Frameworks

We can use it to modularize your application, being able to package up and re-distribute in multiple projects and work with reusable components.

I like to work using frameworks and creating their own target. Thus, a benefit to it, it's for each change inside the framework, only the framework will be rebuilt. So we can save time of build and also letting the project better organize to team work.

## Modules Strategies

Two categories that fit my needs regarding modularization, kit and feature modules both categories are welcome too many projects focus on solid principles and clean architecture.

There it is a short explanation about these categories that I took from another blog post:

- Feature modules: Modules that represent a feature of your app. For example, you could create a module Account for your customer account part.
- Kit modules: Modules that represent a technical part of your app. You could have for instance a Network modules which handles the networking layer, a UIComponent module representing the UI elements of your app, a Localization module for your wordings… You can eventually create a Core module for everything that is connected to many parts of your application and is too hard to isolate. 
If you have a local database, maybe a Storage module could be convenient to handle the database requests.

A feature module should obviously import one or more kit modules. A Kit module should NOT import a feature module. And a feature module should not import another feature module.

## Modularizing spaceX

To create the framework, let's create the target as well. Just go onto “File -> New -> Target” and choose Framework. 

For spaceX project I had used feature modules and kit modules as shown below:


<div align="center">
<img src="https://github.com/Hugo-Coutinho/Modular-SpaceX/blob/master/ReadmeFiles/01.png?raw=true"/>
<img src="https://github.com/Hugo-Coutinho/Modular-SpaceX/blob/master/ReadmeFiles/02.png?raw=true"/>
</div>


- SpaceX: Main project
- Launch: Feature module with all that regarding Home Screen 
- UIComponent: Kit module with all UIKit components 
- Core: Kit module focus on business logic
- Network: Kit module focus on API requests

Now, my main target depends on all of the others frameworks. You must add up these frameworks in Target -> Build Phases -> Dependencies


<div align="center">
<img src="https://github.com/Hugo-Coutinho/Modular-SpaceX/blob/master/ReadmeFiles/03.png?raw=true"/>
</div>


When your module needs to other dependencies, you can add up like you did with the main Target, no worries. Although, just remember that kit module should not import a feature module. And a feature module should not import another feature module.


<div align="center">
<img src="https://github.com/Hugo-Coutinho/Modular-SpaceX/blob/master/ReadmeFiles/04.png?raw=true"/>
</div>


Now that our frameworks are created, we want to use this class outside of our framework we need to mark it as public.


<div align="center">
<img src="https://github.com/Hugo-Coutinho/Modular-SpaceX/blob/master/ReadmeFiles/05.png?raw=true"/>
</div>
