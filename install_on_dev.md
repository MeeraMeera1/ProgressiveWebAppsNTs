
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

>Above fields are mandatory to make the add to home screen dialog appear.

#### name/short_name

Value used under the app icon once installed on user's device. 
Short name is used if not enough space is available.
Best to keep it under 12 characters.
>In Chrome, the app name is also used on the splash page screen and is displayed while the PWA is loading.  

#### start_url

The path to the assets, which should be loaded when the app is launched. Useful in that we want our app to always start from the same page.  
>Adding a query string to the URL can provide a web analytics tool with some context information and determine how many users accessed the web app via the icon on the home screen. Provides more info about user behavior.  

#### display 

Specifies how the app should be displayed in the browser.
Different values provide different browser experiences: <br>
+ browser : provides a standard browser experience 
+ standalone : app opened in independent window, makes PWA look like a native app (address bar no longer visible)
+ fullscreen : uses whole screen of device. No UI browser elements rendered. Suited for games or multimedia apps  

#### icons 

Determine the icons that are used on the device home screen or for the splash screen.  
Icon should be at least 144px.  
Chrome suggests having two icons: one 192px and one with 512px.  
The best approach is to identify our target devices and then add icons with the relative resolution.  
The __purpose__ attr indicates to the user agent what the usage purpose for the icon is.  
3 values can be used at the same time for our purpose. It uses the fallback principle so if one doesn't work there are other options.  
The 3 values are:  
+ badge : user agent could present this icon type when there are space constraints and/or color requirements differ from those of the application icon.
+ maskable : image designed with icon masks and safe zones in mind. Therefore any part of the image that is outside the safe zone is automatically ignored by the user agent. 
+ any : user agent can display the icon in any context.  

#### background_color 

Sets the background color of our app.  
> If PWA is added to the home screen from chrome, the background color is also used for the splash screen.  

## Complimentary Properties 

Properties that are optional but still recommended.  

#### orientation 

Specifies whether the application should be displayed in portrait or landscape mode. Landscape is better for games and media.  

#### theme_color

On mobile devices, it sets the theme color surrounding the site.  
On desktops, the theme color is used to style the title bar.  

#### description

Provides a description for the app.  

#### scope

Scope defines the navigation scope of the websites context. If the user navigates outside the scope, it returns a normal web page inside a browser window.  

#### prefer_related_applications

Allows us to suggest a native app over the PWA. Handy in cases where we have a native app with specific features not covered by our PWA. Suggested to users for a more complete experience.  

#### related_applications 

Provide the details to install the native app from the app or play store.  
Possible object fields are:  
+ platform : chrome_web_store, play, itunes, windows 
+ url : the application store URL
+ id : the application ID to univocally identify the native app on the specified platform  

#### dir 

Describes the text orientation for the name, short name, and description properties. Accepted values are: __ltr__,__rtl__, and __auto__ (default).  

## Manifest Generator Tool 
[Manifest Generator](https://app-manifest.firebaseapp.com/).  

# Conclusion

Why web manifest is important.  
How to use it to define how a progressive app is rendered in the browser.  

