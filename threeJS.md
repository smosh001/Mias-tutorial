# Three.JS Tutorial - Create 3D Environments with HTML and Javascript

![three.js blog](images/screenshots/threeJSblog.jpg)

Check out an example:
[Three.js Blog](https://am0eba-byte.github.io/internshipblog-3js/)

See other awesome things you can do with three.js:
[Three.JS examples page](https://threejs.org/examples/#webgl_animation_keyframes)


## Step 1: *Install the Three.JS Node Package Module using your Terminal/Command Line*
Before we embark on the journey of creating our impressive 3D website, it's essential to set up the necessary tools on the command line. This includes the installation of  `Node.js` and `npm` at the command line.

## 1.1 Install Node.js

Node.js plays a fundamental role in the JavaScript ecosystem. It provides an asynchronous event-driven JavaScript runtime, designed for building scalable network applications, as described by Node.js developers.

Before proceeding with the installation, it's wise to check if you already have Node.js installed on your machine. To do this, open your command line interface.

## 1.2 Optional: Choose Your Development Environment

While Node.js is a crucial part of our toolkit, the choice of development environment can greatly impact your workflow. We strongly recommend considering JetBrains' WebStorm as an alternative to oXygen XML Editor, particularly for intensive JavaScript projects. [JetBrains' WebStorm](https://www.jetbrains.com/webstorm/download/), 

## Step 2: Verify and Set Up Development Environment

## 2.1 Verify Node.js Installation

To begin, it's essential to confirm whether you have Node.js installed on your system. We'll use the integrated terminal in Visual Studio Code (VS Code) for this check.

In the VS Code terminal, enter the following command:

```bash
node -v
```

If Node.js is already installed, the terminal will display a version number, typically in this format: `v0.10.35`.

If you don't see a version number, proceed to install Node.js. It's important to note that Node.js is a free and indispensable tool for any level of JavaScript development, including professional work.

## 2.2 Install Node Package Manager (NPM)**

Now that you have Node.js installed, let's introduce you to the Node Package Manager (NPM). NPM is a vital part of the JavaScript ecosystem, enabling developers to utilize open-source Node.js package modules. These modules empower you to accomplish impressive tasks with JavaScript, such as creating 3D websites. You'll need NPM to install the Three.js package.

Check if NPM is already installed by running this command in your VS Code terminal:

```bash
npm -v
```

Similar to the Node.js check, a version number should appear if NPM is already installed. If not, you'll need to install it using the following command:

```bash
npm install -g npm
```

With Node.js and NPM in place, you're now ready to set up your project repository.

## 2.3 Create a Project Directory and Install VITE

Begin by creating an empty project directory. Once the directory is established, open the command line within it and enter the following command:

```bash
npm init vite
```

Follow the on-screen prompts:

- Name your project.
- For the package name, you can press Enter to accept the default.
- Select the "vanilla" framework (indicated in yellow).
- Choose "JavaScript" as the language (indicated in yellow).

Note: If arrow key selection isn't functional on your Windows computer, consider using Windows Powershell or Windows Terminal instead of Git Bash.

Executing this command will generate new files within your directory.

## 2.4 Install Three.js via Command Line

To work with Three.js, you need to install it via the command line. Enter the following command:

```bash
npm install --save three
```
You should observe the creation of a new `node_modules` directory, a `package.json` file, and a `package-lock.json` file.

Important: It's crucial not to modify or interfere with these files and directories. They contain dependencies automatically managed by NPM, and manual adjustments can lead to issues.

## 2.5 Prepare Your HTML**

To render your 3D world, your HTML should include three essential elements:

1. A `<canvas>` element with a unique `id` attribute, serving as the canvas for your 3D objects.
2. A `<script>` tag with the `type` attribute set to "module" and the `src` attribute pointing to your JavaScript file (usually named `main.js`), which contains the 3D instructions.
3. A `<main>` element for text content overlaying your 3D environment.

Here's an example of how this should be structured:

```
<!DOCTYPE html>
<html>
    <head>
        <title>Three JS Demo</title>
        <meta charset="UTF-8" />
        <meta name="author" content="Mia Borgia" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <link rel="stylesheet" type="text/css" href="threeJSstyle.css" />
    </head>
    <body>
        <canvas id="bg"></canvas>
        <script type="module" src="./main.js"></script>
        <main>
            <header>
                Welcome to the world of Three.JS!
            </header>
            <section>
                <div>
                    <p>
                        The possibilities are endless! 
                    </p>
                </div>
            </section>
        </main>
    </body>
</html>
```

Here's a more logical and systematic version of the provided text:

## Step 3: Configure Your Background Canvas with CSS

In your project directory, alongside your `index.html` file, you should locate a CSS file named `style.css`. To set your canvas element as the background of your site, add the following code to your `style.css`:

```css
canvas {
  position: fixed;
  top: 0;
  left: 0;
}
```

This CSS code will ensure that the `<canvas>` element in your HTML serves as the background for your website. This canvas will be the canvas on which your 3D objects will be displayed as you create them using JavaScript.

## Step 3: Viewing Your Site Locally

Since Three.js relies on dependencies for rendering, you need to run your application in the command line whenever you make changes to view it locally.

In your command line terminal, execute the following command:

```bash
npm run dev
```

This command will generate a localhost link in the command line. Copy this link and paste it into your web browser to view your application locally.

## Step 4: Writing JavaScript Code

In your `main.js` JavaScript file, you'll need to import the Three.js node package module to access the pre-built 3D-building methods and objects. Simply add these import statements at the beginning of your JS file:

```javascript
import * as THREE from 'three';
```

## Step 5: Setting Up Your Three.js Scene

You'll require three main components to configure your Three.js scene:

1. A new scene.
2. A camera.
3. A renderer.

These objects can be declared as constants in JavaScript using the `new THREE` methods:

```javascript
// Scene Setup
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer({
  canvas: document.querySelector('#bg'),
});
```

However, your new scene won't be visible until you render it using the `.render` method:

```javascript
renderer.render(scene, camera);
```

Once these constants are set, you can manipulate them using Three.js's built-in methods. For example, you can adjust the pixel ratio, size, and camera position as needed:

```javascript
renderer.setPixelRatio(window.devicePixelRatio);
renderer.setSize(window.innerWidth, window.innerHeight);
camera.position.setZ(50);
camera.position.setX(-3);
```

## Step 6: Creating Your First 3D Object

With your scene prepared, you can begin adding 3D objects. To create a 3D object in Three.js, you'll need three essential components:

1. The geometry.
2. The material.
3. The mesh (a combination of geometry and material).

You should create constants for each of these components to manipulate and add the final mesh to your scene. Here's an example of creating a basic cube:

```javascript
const geometry = new THREE.BoxGeometry(10, 10, 10);
const material = new THREE.MeshBasicMaterial({ color: 0xFF6347 });
const cube = new THREE.Mesh(geometry, material);

scene.add(cube);
```

You can change the position and rotation of your object by manipulating the cube's properties:

```javascript
cube.position.z = -15;
cube.position.x = -15;
cube.rotation.x = 2;
cube.rotation.y = 0.5;
```

## Step 7: Lights and Material Types

Three.js provides various material types and textures for objects. Some materials require light sources in the scene to be visible. For instance, the Phong material requires light. Here's how to create and add a light source to your scene:

```javascript
// Lights
const pointLight = new THREE.PointLight(0xffffff);
pointLight.position.set(0, -10, 10);

const ambientLight = new THREE.AmbientLight(0xffffff);
ambientLight.position.set(25, -15, -400);

scene.add(pointLight);
scene.add(ambientLight);
```

Point lights emit light in a specific direction, while ambient lights diffuse light in all directions. You can change the light color by adjusting the HEX code value in the `THREE.Light()` object's parameters.

If you switch your cube's material to `THREE.MeshStandardMaterial`, it will accept light, unlike `THREE.MeshBasicMaterial`. For example:

```javascript
const material = new THREE.MeshStandardMaterial({ color: 0xFF6347 });
```

This step concludes the setup and initial object creation in your Three.js project.
![standard material cube](images/screenshots/standardMaterial.jpg)


# Animate your scene

To make your objects move through time, we need to create a new `animate` function and set our animation properties within it.

You can animate just about any property of an object you want.

```
function animate() {
	requestAnimationFrame( animate );

    // slowly rotate the cube:

    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    // rotate the icosahedron a little faster in the opposite direction:

    icoMesh.rotation.z += -0.03
    icoMesh.rotation.y += -0.03

	renderer.render( scene, camera );
}
```

You must call the animate() function in order to tell the browser to use it:
```
animate();
```

Congratulations! Your scene should now look something like this:

![three.JS object screenshot](images/screenshots/twoObjects.jpg)



## Three.JS Helpers

Three.JS comes with a wide variety of scene helpers to assist in orienting the view of your scene. 

We can add a **Light Helper**, which shows us where in the scene our light objects are positioned.

Let's add a light helper to our `pointLight` object:

```
// Helpers

const lightHelper = new THREE.PointLightHelper(pointLight);

scene.add(lightHelper)
```
![light helper](images/screenshots/lightHelper.jpg)


We can also add a **Grid Helper** to show the 3D axes of our scene.

```
const gridHelper = new THREE.GridHelper(200,50);

scene.add(gridHelper)
```


## Orbit Controls

Three.JS has various types of Control methods to allow you to add interactive functionality to your scene. 

Let's add an `Orbit Control`, which will allow us to move our camera and traverse our scene with mouse controls and zoom.

In order to add the Orbit Controls as a function, we need to import that package from the three.js dependencies. At the top of your document where you imported THREE.JS, (directly underneath `import * as THREE from 'three';`) add this line of code:

```
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';
```

Then, under your `Helpers`, activate your orbit controls by declaring it as a constant:

```
// Orbit Control

const controls = new OrbitControls(camera, renderer.domElement)
```

Your orbit controls will not be functional until you add an `.update()` method to your new `controls` object WITHIN your `animate(){}` function:

```
function animate() {
	requestAnimationFrame( animate );

    // slowly rotate the cube:

    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    // rotate the icosahedron a little faster in the opposite direction:

    icoMesh.rotation.z += -0.03
    icoMesh.rotation.y += -0.03

    // ALLOWS YOUR ORBIT CONTROLS TO UPDATE LIVE IN REAL-TIME:
    controls.update()

	renderer.render( scene, camera );
}
```

When you refresh your server, you should now be able to click and drag to orbit the camera view of your scene!

## Scene Backgrounds

We can set our scene backgrounds to whatever we want, using regular image files. 

- create a new folder in your project and name it `images` 

- find a cool, high-resolution image that you'd like to appear as the background of your scene. We are using this one:

![night sky background photo](images/night_sky.jpg)

- save the image file of your choosing inside your new `/images` directory.

- create a new `Texture` object by referencing your image, and add it to the scene:

```
// Background

const spaceTexture = new THREE.TextureLoader().load('images/night_sky.jpg')

scene.background = spaceTexture;
```
![background texture scene](images/screenshots/backgroundTexture.jpg)



## Texture Mapping

In the world of 3D modeling, `Texture Mapping` refers to mapping flat images onto the surface of a 3D object. Three.JS allows us to do this by creating `Texture` objects and applying them to our 3D objects using methods.

Find an image file that you'd like to apply to the surface of a new object. We will be using this one:

![smiley face texture](images/smile.jpg)

Save your texture image file in your `/images` directory.

Now, in our `main.js`, let's create a new texture that we will map onto a new object:

```
// Object texture mapping

const smileTexture = new THREE.TextureLoader().load('images/smile.jpg')
```

Now, let's create a new `Sphere` object to map our new texture onto. 

**Remember** new objects require three basic components:

- a `geometry`
- a `material`
  - in this case, our new `BasicMaterial` will have a value of `{map: smileTexture}` instead of a color hex code.
- a `mesh`, which combines the `geometry` and `material` to create the final visible object.

```
// Object texture mapping

const smileTexture = new THREE.TextureLoader().load('images/smile.jpg')

const sphereGeometry = new THREE.SphereGeometry( 10, 22, 10 );

const smileMaterial = new THREE.MeshBasicMaterial({map: smileTexture})

const smileMesh = new THREE.Mesh(sphereGeometry, smileMaterial);

scene.add(smileMesh);
```

![new texture-mapped object](images/screenshots/textureMapping.jpg)

You can manipulate the object's static position, rotation, and size as you wish, the same as your other objects.

You can also add property changes to this new texture to be animated in real-time in your `animate()` function:

```
function animate() {
	requestAnimationFrame( animate );

    // slowly rotate the cube:

    cube.rotation.x += 0.01;
    cube.rotation.y += 0.01;

    // rotate the icosahedron a little faster in the opposite direction:

    icoMesh.rotation.z += -0.03
    icoMesh.rotation.y += -0.03

    // rotate the smiley sphere on the Y axis:

    smileMesh.rotation.y += 0.05

    controls.update()

	renderer.render( scene, camera );
}
```

### Normal Texture Mapping

Three.JS also allows you to create vivid textures to alter the surface shape of your mesh to create real, light-reactive textures on your objects.

To do this, we need to create a **normal**. 

**Normal mapping** in the 3D world refers to a texture mapping technique used for faking the lighting of bumps and dents – an implementation of bump mapping. It is used to add details without using more polygons.

To create a normal, you must first find a texture image you like that can be converted into a normal.

We used this site to generate and customize a texture:
[Texture Generator Online](http://cpetry.github.io/TextureGenerator-Online/)

Here's the texture we generated:

![texture](images/texture.png)

Now, we must convert this texture image file into a normal map. We used this site to upload our texture image file and have it converted into a normal:
[Normal Map Online](https://cpetry.github.io/NormalMap-Online/)

Here's the normal map that was generated from our image:
![normal map](images/textureNormal.png)

Now we need to create a new `normalTexture` object in our Javascript by loading a new texture and loading in our normalMap image file:

```
const normalTexture = new THREE.TextureLoader().load('images/normals/textureNormal.png');
```

Now, to apply our normal map to a new object, we must apply our normal map image to the `normalMap` property within our new `MeshStandardMaterial`. 

```
// Normal Texture Map

const torusGeo = new THREE.TorusKnotGeometry( 5, 1, 250, 5, 9, 15 );
const torusMaterial = new THREE.MeshStandardMaterial( { 
  normalMap: normalTexture,
  roughness: 0,
  metalness: .8
} );

const torusKnot = new THREE.Mesh( torusGeo, torusMaterial );

scene.add( torusKnot );
torusKnot.position.y = 20

```

We also added a `roughness` and `metalness` property value to make our new object look more shiny and reflect light. Your scene should look something like this:

![normal mapping](images/screenshots/normalMapping.jpg)
