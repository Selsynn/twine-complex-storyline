# twine-complex-storyline
Using Twine to have complex and non-linear storyline. Provides a custom quest system. 

## What it is ? 
Twine is a system to have interactive story that is pretty straightforward. But I found it hard to have some story format.

### Caracteristic of the story format with this project
Player can  pretty always navigate between some passages (Permanent passage) and on everywhere, can begins quest that needs to be played at different places. \
Exemple :\
There is a home, a room, and a garden. This are *permanent passages*. In the room, a *quest* can be found that requires some herbs from the garden. \
In traditionnal Twine working, we will have to copy link to the garden, for this quest or edit garden to see a variable and display the quest to search the herbs. \
With this framework, writers/game-master have to define home, room and garden as *permanent passages*, and create passage to the first element of the *quest* to the room, and from here (from the first "quest" passage  will define where the others will appear)

### How-to ?
#### Init a project
You need Twine, v2, and format Snowman (pure js)\
Create a new story. \
In the launch passage add the fellowing between tag for js : <% and %>\
```javascript
class Quest{
	constructor(target,condition){
		this.target = target;
		this.condition=condition;
	}
}

s.quest = [];
```
It's very simple, in this first version, we create a structure that will host our quest, and create a global variable that will hold them.
#### Create a permanent passage 
New Passage via Twine.\
And when you edit the passage, take care to have a description that will be quasi permanent throughout the story. \
Add to the end the fellowing between tag for js (<% and %>)\
```javascript
_.each(s.quest['XXXX'],function(quest){
	if(quest.condition()){
		%><p><%=quest.target%></p><%
	}
});

s.back="[[YYYYYYY]]";
```
Change XXXX by your referential for this permanent passage.\
Change YYYYYYY by your referential for this permanent passage that will be displayed to the player. (Backing link)\

Re-open your init passage and add after initializing s.quest
```javascript
s.quest['XXXX']=[];
```
It will initialize the list of quest you will find for this permanent passage.

#### Create a quest
```javascript
s.quest['XXXX'].push(new Quest("ZZZZ", function(){return true;}));
```
Change XXXX by the referential of your permanent passage, and ZZZZ by a link to the passage that begins the new quest. Note that Twine will link the quest from where this is added. \
If you add this line from your init, it will be separated from your permanent passage.
## Features
At length, this project might be a new format for Twine. 

### Core Features 
- [x] Quest system 
- [ ] Inventory system 
- [ ] Reputation system 
- [ ] Example in english  
- [ ] Overlay of Twine to see all storyline for quests, and all storyline for permanent passages 

### Secondary Features
- [ ] 

 
