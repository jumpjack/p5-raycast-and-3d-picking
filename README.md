# p5-raycast-advanced (WORK IN PROGRESS)

A function for 3d picking of objects in WEBGL mode in p5js.

In the original version, a ray is drawn from camera to the world, perpendicular to camera plane (hence visible as single point to the user), with length **rayDistance**; then it is calculated the 3d distance from the far tip of the ray to a specific position (**objectPosition**, an array `[x, y, z]`), which represents the center of the object; such distance is compared to a threshold (**objectRadius**); the object is cobnsidere "picked" if the measured distance is smaller than the threshold.

But this can cause false negatives: 

![image](https://github.com/jumpjack/p5-raycast-and-3d-picking/assets/1620953/2d458750-0c72-4d9b-b946-f75c2fd9e538)

Although the user sees the cursor overlapping the object, the ray tip could be very far from object, preventing its picking.


In the "advanced" version, the distance is calculated between the object position and the whole ray, thuse preventing false negatives; the length of the ray is not determined by the call but defined inside the function.

Anyway also this version has its limit: it works perfectly with spherical objects, it works approximately with prismatic object, it works poorly with objects with different sizes in the 3 directions, such as flat objects: for flat objects a ray/plane intersection version is under study.


## Installation

Add to the HEAD section of your HTML page the script and its dependencies:
 - <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/11.8.1/math.js" integrity="sha512-5nftKkjZO1gtHEWFlUGXi/vuXzFnWTom549IH/gMqOiJHcPfH5z/1DO8/c0qnoG0R8RCVLOeBDXhCjg2+23nqQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
 - <script src="https://cdn.jsdelivr.net/npm/p5-raycast@1.0.1/p5-raycast.js"></script>


## Usage


Define a camera variable called `cam` in the setup function
```javascript
cam = createCamera();
```

Call **raycast(rayDistance, objectPosition, objectRadius)** :

- `rayDistance`: the length of the ray that will be cast into the 3D scene through the mouse position.
- `objectPosition`: An array `[x, y, z]` defining the position of the object you want to select in world space.
- `objectRadius`: The distance from the object's position which is considered a "hit".

Result is a boolean (picked/not picked)
 

## License

[MIT](https://choosealicense.com/licenses/mit/)
