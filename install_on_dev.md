
# Web App Manifest 

* The web manifesto provides metadate to instruct the browser about how the PWA should be rendered and displayed on a users device. *

> Basically information about the web app that is stored in a JSON file that makes the app downloadable 

Typically the manifest file is stored at the root of the app named: __manifest.json__ or __anythingYOUWant.webmanifest__.  

To associate said manifest to the app it has to be added to a link tag in the head section of an HTML doc.  

The request for the manifest is made without any credentials. Thefore, if the manifest requires credentials a __crossorigin="use-credentials__ attribute should be provided.   

> if the attribute is not present, the resource is fetched without a CORS request.  

## File Structure

    {
        "short_name": "MyCoolPWA",
        "name": "My cool Progressive Web App",
        "orientation": "landscape",
        "description": "A simple experiment with PWAs",
        "background_color": "#3367D6",
        "theme_color": "#3367D6",
        "scope": "/",
        "start_url": "/?source=pwa",
        "display": "standalone",
        "icons": [
            {   
                "src": "/images/icons-144.png",
                "type": "image/png",
                "sizes": "144x144",
                "purpose": "maskable any"
            },    
            {
                "src": "/images/icons-192.png",
                "type": "image/png",
                "sizes": "192x192",
                "purpose": "maskable any"
            },
            {
                "src": "/images/icons-512.png",
                "type": "image/png",
                "sizes": "512x512",
                "purpose": "maskable any"
            }
        ],
        "prefer_related_applications": true,
        "related_applications": [
            {
                "platform": "itunes",
                "url": "https://itunes.apple.com/app/native-app/id345"
            },
            {
                "platform": "play",
                "id": "com.my-domain.native"
                "url": "https://play.google.com/store/apps/details?id=com.my-domain.native",
            }
        ],
        "dir": "ltr"
    }