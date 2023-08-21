# Create the NextJs App ( Repo )

##### First Create a nextJs application with the below command. I will name the repo as PWA.

```
npx create-next-app pwa
```

##### Then install the next-pwa package from npm. You can use the below command.

```
npm i next-pwa
```

# next.config.json file

##### Then check is the next.config.json file available or not. If it is not available create the file at the root level. So now everyone has the next.config.json file. Now edit the file like below.

#

```typescript
// Note : To required('next-pwa') you should install that package as explain
// above. If you miss that please install it with npm i next-pwa command.

const withPWA = require("next-pwa")({
  dest: "public",
  register: true,
  skipWaiting: true,
  disable: process.env.NODE_ENV === "development",
});

const nextConfig = withPWA({
  reactStrictMode: true,
  swcMinify: true,
});

module.exports = nextConfig;
```

#

##### Below I am adding an image of a next.config.json file. So if anyone can understand it should add in the root level and its code.

#

![next.config.json](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*XCExd5E12Dc8CGtyYBP_vg.png)

#

# Now go to the public folder of the Repo

#### Then follow the below steps.

#

- create a file called manifest.json inside the public folder. Then add the below code.

#

```typescript
//You can change the name, short name, description like properties the way
// you want. please note icons are very important here.
// If you did not add it correctly you will get an error and PWA will not
// work with your project.

{
  "name": "My Next.js PWA",
  "short_name": "NextPWA",
  "description": "A sample Next.js Progressive Web App",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#000000",
  "icons": [
    {
      "src": "/icon.png",
      "sizes": "512x512",
      "type": "image/png"
    },
    {
      "src": "/icon.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable"
    }
  ]
}
```

#

#

- Added an image to the public folder with the correct name and the correct dimensions that you provided in the icons array in the manifest.json file.

#

```typescript
// If your icons array is look below.

"icons": [
    {
      "src": "/icon.png",
      "sizes": "512x512",
      "type": "image/png"
    },
    {
      "src": "/icon.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable"
    }
  ]

// You should add an image with
// - name icon.png
// - dimensions - 500x500 (canva can be used to get images with dimensions)
// - type image/png
```

#

#### Below I am attaching the image of mainfest.json and icon.png file so you can see the correct level.

#

![manifest.json](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*8CmDSnvx-mthlsdjmgHoiw.png)

#

# Then go to the \_document.tsx or \_document.jsx file of your Repo.

#### Added the below metadata and the link tags inside the <Head> tag.

```typescript
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<meta name="theme-color" content="#000000" />

{/* make sure to provide the name of your icon in below.*/}
<link rel="apple-touch-icon" href="/icon.png" />
<link rel="manifest" href="/manifest.json" />
```

##### Below is the image of that code.

![_document.tsx](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*dntgXrGDUmz0hN00IpJbvQ.png)

#

# Now all done. Let’s build the app with the npm run build.

```
npm run build
```

##### And start the production server with npm run start.

```
npm run start
```

# Now you can see your PWA like below and install it on your desktop or mobile.

#### Desktop

![PWA](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4xGyEJcuUWMHCqPKVMp6FQ.png)

#

#### Mobile

- Add to Home Screen from Website

![Add to home](https://cdn-images-1.medium.com/max/1600/1*YdizLAwFjthafKlyNsYu1g.jpeg)

#

- PWA from mobile

![pwa-mobile](https://cdn-images-1.medium.com/max/1600/1*v2eulVSqgmKXfvtGxiaEbQ.gif)

#

# In case you can’t see the PWA

![error](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*qrtxx46erHxBxl8oJSAZRQ.png)

#

# Google Lighthouse PWA check

#

![Google Lighthouse Test](https://cdn-images-1.medium.com/max/1600/1*nKAb5CnaJemqpX12pmW2sQ.png)

##### If you can’t see right-click your browser and click the inspect. Then go to the application tab. Then you can see the errors or warning like below in the Manifest file. That means you did something wrong and please follow the steps correctly again.
