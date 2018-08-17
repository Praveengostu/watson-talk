#Watson-talk

Set up an application to leverage the Watson Tone Analyzer service. 


# 1. Build the `watson-talk` image.

   ```docker build -t registry.ng.bluemix.net/<namespace>/watson-talk ./watson-talk```

2. Push the `watson-talk` image to IBM Cloud Container Registry.

   ```docker push registry.ng.bluemix.net/<namespace>/watson-talk```

3. In watson-deployment.yml, update the image tag with the registry path to the image you created in the following two sections.

   ```yml
       spec:
         containers:
           - name: watson
             image: "registry.ng.bluemix.net/<namespace>/watson" 
             # change to the path of the watson image you just pushed
             # ex: image: "registry.ng.bluemix.net/<namespace>/watson"
   ...
       spec:
         containers:
           - name: watson-talk
             image: "registry.ng.bluemix.net/<namespace>/watson-talk" 
             # change to the path of the watson-talk image you just pushed
             # ex: image: "registry.ng.bluemix.net/<namespace>/watson-talk"
   ```