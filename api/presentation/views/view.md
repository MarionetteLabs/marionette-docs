### View  
Extends from `Backbone.View`

> The Marionette View is a 'background Class'. Background Classes are named because you don't usually
instantiate a Background Class by itself. Instead, other Classes extend from, or include the Background
Class functionality into their own API. Long-story short: you shouldn't ever need to call `new BackgroundClass`.
> All of the other Marionette View classes extend from Marionette.View. You are not recommended to use this Class.

Views are arguably one of the weakest parts of Backbone, and by no coincidence one of the strongest parts of
Marionette. The four Marionette views all extend from this central base Class to gain access to shared
API and properties. Note that a Marionette.View will not work by itself; it is merely the skeleton of the
four other views. The API here is duplicated in the other four Views' API; it is merely here for completeness.


