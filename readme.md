 is a Node.js module is based upon standard Sugar 7 sugarapi.js library used by our Sidecar framework. It has been modified to allow it to work within a Node environment. Using this module, you'll be able to easily make Sugar 7 REST API calls from your own Node applications. Check out the README for more usage details.
 
 
 
 #Examples
 

 ```
 //Initialize
  var sugarcrm = require('sugarcrm');
  var sugarApi = sugarcrm.Api.getInstance({
                 defaultErrorHandler: (opts && opts.defaultErrorHandler) ? opts.defaultErrorHandler : SUGAR.App.error.handleHttpError,
                 serverUrl: _app.config.serverUrl,
                 platform: _app.config.platform,
                 timeout: _app.config.serverTimeout,
                 keyValueStore: _app[_app.config.authStore || "cache"],
                 clientID: _app.config.clientID
             });
  //Login - store session
  sugarApi.login(credentials, info, {
                  success: function(data) {
                      sugarApi.trigger("app:login:success", data);
                      //do something with data
                  },
                  error: function(err) {
                      sugarApi.error.handleHttpError(error);
                      console.error(error)
                      //do something with error
                  }
              });        
             
  sugarApi.records(
                    method,
                    model.module,
                    method == "update" || method == "create" ? this.getEditableFields(model, options.fields) : model.attributes,
                    options.params,
                    {success: function(data){
                    },
                    error: function(err){
                       console.log(err);
                    }
                    }
                    );

    
 ```
 
 
 