---
context:
  - "[[Computer Graphics]]"
---

#empty

# Lighting (Computer Graphics)

Encompasses the range of techniques used to simulate light within [[Computer Graphics]].

---

Lighting models simulate how light interacts with surfaces to provide crucial visual effects like shape, depth, color, spatial relationships, material, and so on.

**Light Attenuation**: Refers to the gradual loss of light intensity with distance.

## Lighting Models

Blinn-Phong model (the standard)

PBR (Physically-Based Rendering)

## Light Sources

- **Point Light**: Eminates from a single point outward in all directions.
- Directional Light
- Spot Light

---

Specular Reflection:

- Phong model
- Blinn-Phong model

Specular reflection is like a mirror, reflecting light in a direction.

Diffuse


---

Specular light wants to know the location of the viewer, to see how close the eye is to the direction of the perfect mirror bounce.

For diffuse the location of the viewer is not relevant.

---

1. Ambient

This is the general, overall light in the room.

    What it is: Light that has bounced off the walls, ceiling, and other objects so many times that it seems to come from everywhere. It's the reason you can see the shadowy side of the apple at all.

    Simple Analogy: The "background hum" of light. It uniformly lights everything a little bit.

    On the apple: It's the dim, base red color you see on the parts of the apple that are in complete shadow. Without ambient light, those parts would be pure black.

2. Diffuse

This is the main color of the object under direct light.

    What it is: The light that hits a surface and scatters in all directions. Because it scatters, it looks the same from every viewing angle. It defines the object's base color and is affected by the angle of the light.

    Simple Analogy: The matte, non-shiny paint on a wall. It looks the same color no matter where you stand in the room.

    On the apple: It's the bright, true red color on the side of the apple facing the light source (like a lamp or the sun).

3. Specular

This is the bright, shiny highlight.

    What it is: The light that hits a smooth, shiny surface and reflects directly into your eye, like a mirror. It's usually white or the color of the light source, not the color of the object. It moves across the surface as you change your viewing angle.

    Simple Analogy: The blinding white glint on a polished car or a glass window.

    On the apple: It's the small, bright white spot on the curviest, shiniest part of the apple.
