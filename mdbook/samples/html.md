```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>title</title>
    <link rel="stylesheet" href="heat.css">
    <script src="dist/heatTS.js"></script>
  </head>
  <body style="width:1024px;height:768px">
    Heat.Js
      <script>
            var storageProvider = new Heat.StorageProviderLocal({});
            var options = {
                "interactionHandlers":[Heat.InteractionHandlerClick],
                "storageProvider":storageProvider
                          };
            var heatTrap = new Heat.HeatTrap(options);
            console.log(heatTrap.getAppVersion());
          
            heatTrap.on("test",function(){
                console.log("test fired");
            },this);
            
      </script>
  </body>
</html>```

This is how you do something in HTML