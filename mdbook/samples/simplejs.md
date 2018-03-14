Blah blah this is a js code sample of how to do it
```JavaScript
window.heat = window.heat || {};

(function(window,heat){
    /*uses grunt-explainjs method doc*/
    'use strict';
    
    /*jshint camelcase: false */
    function StorageProvider(options){
        var _self = this;
        this.subscribers = [];
        options = options || {};
        //options.appName = options.appName || "Heat map test" // set default
        //options.interactionHandlers = options.interactionHandlers || [] // set default
        
        /*jshint unused:false */
        /**
         * function to store a new record
         *
         * @param {InteractionEvent}
         */
        this.storeNewRercord = function(newRecord) {
        };
        
        //Constructor 
    }
    
    heat.StorageProviderSling = heat.StorageProviderSling || StorageProvider;
        
})(window,window.heat);
```