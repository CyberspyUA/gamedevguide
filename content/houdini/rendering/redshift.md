# Redshift
## Compositing Equation

- Beauty = DiffuseFilter_DiffuseLightingRaw + DiffuseFilter_GlobalIlluminationRaw + DiffuseFilter\*SubsurfaceScatteringRaw + SpecularLighting + Reflections + Refractions + Emission + Caustics
- If using "Caustics Raw" instead of "Caustics", these would have to also be multiplied by "Diffuse Filter".
- [Redshift Doc](https://docs.redshift3d.com/display/RSDOCS/AOV+Tutorial?product=houdini)
- Volume AOVs
  - **Multiply** the primary AOV composite by the Volume Fog Tint AOV
    - Volume Fog Tint AOV is a multiplicative layer/volume transmittance
  - **Add** the Volume Lighting AOV to the primary AOV composite.
    - Additive layer that contains only the volume lighting information
  - **Add** the Volume Fog Emission AOV to the primary AOV composite.
    - Additive layer that contains only the emission component

## Volume Rendering

- If want to make volume darker but preserve approximate intensity, adjust scatter and absorption coefficients together
- use the "Scatter Tint" to adjust the overall color of the volume
- advanced manipulation of scattering can happen vie the scatter color ramp to remap density to different color
- Absorption also can be remapped. Its a scalar as it's conceptually remapping opacity

![](https://docs.redshift3d.com/download/attachments/5505683/worddavd9206ac4a12547a3d54af27b86ffcb82.png?version=1&modificationDate=1490834019987&api=v2)<br/>
*Scatter=5, Absorption=5*

![](https://docs.redshift3d.com/download/attachments/5505683/worddavdaa94184008061824b3600c9e8126921.png?version=1&modificationDate=1490834019971&api=v2)<br/>
*Scatter=5=10, Absorption=10*

![](https://docs.redshift3d.com/download/attachments/5505683/worddavbfe7d1f9d04f5e9f273d4528e0822933.png?version=1&modificationDate=1490834020003&api=v2)<br/>
*Scatter=5=10, Absorption=5*

![](https://docs.redshift3d.com/download/attachments/5505683/worddava4db9682e10acdc000cdb9754216549a.png?version=1&modificationDate=1490834020020&api=v2)<br/>
*Scatter=5=3, Absorption=3, ScatterTint=Blue*
