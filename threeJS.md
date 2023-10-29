## Mastering Three.JS: Crafting 3D Worlds with HTML and JavaScript: A Three.Js Tutorial

![threeJSblog](https://github.com/smosh001/Mias-tutorial/assets/98389984/a2ccb950-7ef9-4347-94fe-1f6f8db09625)

Take a look at a demonstration:

[Three.js Blog](https://am0eba-byte.github.io/internshipblog-3js/)

Explore additional amazing possibilities achievable with three.js:

[Three.JS examples page](https://threejs.org/examples/#webgl_animation_keyframes)

## Step 1: *Install the Three.JS Node Package Module using your Terminal/Command Line*
Before we embark on the journey of creating our impressive 3D website, it's essential to set up the necessary tools on the command line. This includes the installation of  `Node.js` and `npm` at the command line.

1.1 Install Node.js

Node.js plays a fundamental role in the JavaScript ecosystem. It provides an asynchronous event-driven JavaScript runtime, designed for building scalable network applications, as described by Node.js developers.

TIP: VS code actually has a command line terminal built into the editor that you can use as well:

![VScodeTerminal](https://github.com/smosh001/Mias-tutorial/assets/98389984/4b2dc869-ec2b-4c9f-b459-599c6011f248)

Before proceeding with the installation, it's wise to check if you already have Node.js installed on your machine. To do this, open your command line interface.

1.2 Optional: Choose Your Development Environment

While Node.js is a crucial part of our toolkit, the choice of development environment can greatly impact your workflow. We strongly recommend considering JetBrains' WebStorm as an alternative to oXygen XML Editor, particularly for intensive JavaScript projects. [JetBrains' WebStorm](https://www.jetbrains.com/webstorm/download/), 

## Step 2: Verify and Set Up Development Environment

2.1 Verify Node.js Installation

To begin, it's essential to confirm whether you have Node.js installed on your system. We'll use the integrated terminal in Visual Studio Code (VS Code) for this check.

In the VS Code terminal, enter the following command:

```bash
node -v
```

If Node.js is already installed, the terminal will display a version number, typically in this format: `v0.10.35`.

If you don't see a version number, proceed to install Node.js. It's important to note that Node.js is a free and indispensable tool for any level of JavaScript development, including professional work.

2.2 Install Node Package Manager (NPM)

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

2.3 Create a Project Directory and Install VITE

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

2.4 Install Three.js via Command Line

To work with Three.js, you need to install it via the command line. Enter the following command:

```bash
npm install --save three
```
You should observe the creation of a new `node_modules` directory, a `package.json` file, and a `package-lock.json` file.

Important: It's crucial not to modify or interfere with these files and directories. They contain dependencies automatically managed by NPM, and manual adjustments can lead to issues.

2.5 Prepare Your HTML

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

## Step 4: Viewing Your Site Locally

Since Three.js relies on dependencies for rendering, you need to run your application in the command line whenever you make changes to view it locally.

In your command line terminal, execute the following command:

```bash
npm run dev
```

This command will generate a localhost link in the command line. Copy this link and paste it into your web browser to view your application locally.

## Step 5: Writing JavaScript Code

In your `main.js` JavaScript file, you'll need to import the Three.js node package module to access the pre-built 3D-building methods and objects. Simply add these import statements at the beginning of your JS file:

```javascript
import * as THREE from 'three';
```

## Step 6: Setting Up Your Three.js Scene

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

## Step 7: Creating Your First 3D Object

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

## Step 8: Lights and Material Types

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

![standardMaterial](https://github.com/smosh001/Mias-tutorial/assets/98389984/0d0b8afb-5d0e-40c9-9cf7-80d503b73d1f)

## Step 9: Animating Your Scene

To make your objects come to life and move over time, you need to create an animate function and specify the animation properties within it. You can animate various properties of your objects.

```javascript
function animate() {
  requestAnimationFrame(animate);

  // Slowly rotate the cube:
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;

  // Rotate the icosahedron a bit faster in the opposite direction:
  icoMesh.rotation.z += -0.03;
  icoMesh.rotation.y += -0.03;

  renderer.render(scene, camera);
}
```

Make sure to call the `animate()` function to instruct the browser to utilize it:

```javascript
animate();
```

Congratulations! Your scene should now exhibit movement as shown below:

![twoObjects](https://github.com/smosh001/Mias-tutorial/assets/98389984/e131b4d6-4b4b-4c79-a573-6a34d6709efa)

## Step 10: Using Three.js Helpers

Three.js provides a range of scene helpers to aid in visualizing your scene's orientation. You can add these helpers as follows:

**Light Helper:**

To visualize the positions of light sources in your scene, you can add a light helper to your `pointLight` object.

```javascript
// Helpers
const lightHelper = new THREE.PointLightHelper(pointLight);
scene.add(lightHelper);
```

**Grid Helper:**

For displaying the 3D axes in your scene, you can add a grid helper.

```javascript
const gridHelper = new THREE.GridHelper(200, 50);
scene.add(gridHelper);
```
![lightHelper](https://github.com/smosh001/Mias-tutorial/assets/98389984/a4bc42c6-7846-4591-bf4b-36e76e603077)

## Step 11: Implementing Orbit Controls

Three.js provides various control methods to add interactivity to your scene. Here, we'll set up Orbit Controls, allowing you to navigate the scene using mouse controls and zoom.

To activate Orbit Controls, import the package and declare it as a constant:

```javascript
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';

// Orbit Control
const controls = new OrbitControls(camera, renderer.domElement);
```

Your Orbit Controls won't be functional until you add an `.update()` method to your `controls` object within your `animate()` function:

```javascript
function animate() {
  requestAnimationFrame(animate);

  // Slowly rotate the cube:
  cube.rotation.x += 0.01;
  cube.rotation.y += 0.01;

  // Rotate the icosahedron a bit faster in the opposite direction:
  icoMesh.rotation.z += -0.03;
  icoMesh.rotation.y += -0.03;

  // Allow your Orbit Controls to update live in real-time:
  controls.update();

  renderer.render(scene, camera);
}
```

Upon refreshing your server, you should be able to click and drag to orbit the camera view of your scene.

## Step 12: Configuring Scene Backgrounds

You can set your scene's background to an image of your choice. Follow these steps:

12.1. Create a new folder named "images" in your project directory.

12.2. Choose a high-resolution image you'd like as the background and save it in the "images" directory. For example, we're using a night sky image.

![night_sky](https://github.com/smosh001/Mias-tutorial/assets/98389984/a8079e86-8af1-4c7c-981e-c909434165ae)

12.3. Create a new `Texture` object and set it as the scene's background:

```javascript
// Background
const spaceTexture = new THREE.TextureLoader().load('images/night_sky.jpg');
scene.background = spaceTexture;
```

Your scene will now have a custom background as shown below:

![backgroundTexture](https://github.com/smosh001/Mias-tutorial/assets/98389984/70844928-69a4-4fcd-abe0-8385768d4a4c)

## Step 13: Texture Mapping

Texture mapping involves applying flat images to the surface of 3D objects. Three.js allows you to create Texture objects and apply them to your 3D objects. Here's how to do it:

13.1. Find an image you'd like to apply to an object's surface and save it in the "images" directory. For example, we'll use a smiley face image.

![smile](https://github.com/smosh001/Mias-tutorial/assets/98389984/ec58abe0-9470-4346-9174-f4f76f55952e)

13.2. Create a new `Texture`:

```javascript
// Object texture mapping
const smileTexture = new THREE.TextureLoader().load('images/smile.jpg');
```

13.3. Create a new 3D object (in this case, a sphere) and apply the texture to it:

```javascript
const sphereGeometry = new THREE.SphereGeometry(10, 22, 10);
const smileMaterial = new THREE.MeshBasicMaterial({ map: smileTexture });
const smileMesh = new THREE.Mesh(sphereGeometry, smileMaterial);

scene.add(smileMesh);
```
![textureMapping](https://github.com/smosh001/Mias-tutorial/assets/98389984/cae91d71-64fb-4743-869d-b69828a9c488)

You can adjust the object's position, rotation, and size as needed, just like with other objects.

## Step 14: Normal Texture Mapping

In the world of 3D graphics, **Normal Texture Mapping** is a technique used in Three.js to create rich and realistic textures that mimic the interaction of light with the surface of 3D objects. This technique is particularly useful for adding depth and intricacy to objects without the need to increase the number of polygons.

To implement normal mapping, follow these steps:

14.1. **Select a Texture:** 

Begin by choosing a texture image that you would like to apply to the surface of your 3D object. This texture will serve as the basis for creating the normal map.

14.2. **Generate a Normal Map:** 

To create a normal map from your chosen texture, you can use online tools such as the **Texture Generator** (http://cpetry.github.io/TextureGenerator-Online/). 
This process involves converting the features and details in your texture into a map that represents how light interacts with the surface.

![texture](https://github.com/smosh001/Mias-tutorial/assets/98389984/77fd5004-27d1-4993-9fc8-9a003c3e5bf5)

Now, we must convert this texture image file into a normal map. We used this site to upload our texture image file and have it converted: **Normal Map Online**(https://cpetry.github.io/NormalMap-Online/)

Here's the normal map that was generated from our image:

![textureNormal](https://github.com/smosh001/Mias-tutorial/assets/98389984/2459e58b-0787-4216-8620-b54c3f3fab2f)

14.3. **Resulting Textures:** 

Once generated, you'll have two images: the original texture and the newly created normal map. These images work in conjunction to give your object a realistic appearance.

14.4. **Create a Normal Texture Object:** 

In your JavaScript code, load the normal map image using Three.js's `TextureLoader`:

```javascript
const normalTexture = new THREE.TextureLoader().load('images/normals/textureNormal.png');
```

14.5. **Apply the Normal Map:** 

Apply the normal map to a new 3D object by including it in the `normalMap` property within a `MeshStandardMaterial`. This step allows your object to respond to light as if it had the detailed features of the normal map.

```javascript
const torusGeo = new THREE.TorusKnotGeometry(5, 1, 250, 5, 9, 15);
const torusMaterial = new THREE.MeshStandardMaterial({
  normalMap: normalTexture,
  roughness: 0,
  metalness: 0.8
});

const torusKnot = new THREE.Mesh(torusGeo, torusMaterial);

scene.add(torusKnot);
torusKnot.position.y = 20;
```

By adjusting properties like `roughness` and `metalness`, you can control how your object interacts with light, making it appear shinier or more reflective, as shown below:

![normalMapping](https://github.com/smosh001/Mias-tutorial/assets/98389984/c4c9d8ce-a7a2-4c50-9ee5-b6737edf10e3)

With these steps, you can achieve a 3D scene with objects that have vivid, light-reactive textures, adding depth and realism to your Three.js project.
