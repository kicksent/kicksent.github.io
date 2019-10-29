## Squash and Stretch(SnS) Animation Script - Unity

For (Vermin)[] I want to use a Animation Principle called Squash and Stretch to make my jumping and other sudden movements feel more expressive.

### However, I have some problems:

- I don't want to have to redraw this for every moving sprite that I have in my game because drawing takes a long time and I am not really an artist.
- I want the rigidbody/hitboxes/children game objects of my gameObject to stay the same so that I dont have unintended side effects
  - Put simply: the SnS effect should be purely visual

### Here's the original plan:

1. Watch some youtube
2. Write a script (or shader) that does SnS
3. Make it loosely coupled so that I can drop it onto any game object that has a rigidbody (and a hitbox?)

### 1. Youtube Videos watched:

##### (Squash & Stretch - 12 Principles of Animation)[https://www.youtube.com/watch?v=haa7n3UGyDc]

- Notes: - More SnS = softer **whereas** less SNS = stiffer - When applying SnS, keep the volume the same

##### Reading

### 2. Script

##### Design:

- [ ] Objects in my game need to have a max fall speed - I can use this max speed to create a range from 0 to 1 of how much stretch I am creating
- [ ] The script needs to check the volume for each stretch so that the volume remains equal throughout - compute a set of values beforehand to avoid recomputing these
- [ ] SnS needs to be based partially on velocity and partially on acceleration
- [ ] Sliders in Unity Editor: - maxSquash, maxStretch, accelerationEffectScale(0 to 1), velocityEffectScale(0 to 1)

- [x] Objects in my game need to have a max fall speed [link](https://forum.unity.com/threads/limit-velocity-of-gravity-when-im-falling.570544/) 1. in FixedUpdate add:
      `rigidbody.velocity = Vector3.ClampMagnitude(rigidbody.velocity, maxVelocity);` **OR** 3. Adjust the Rigidbody2D component Drag property

##### Script

```

```
