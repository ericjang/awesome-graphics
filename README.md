# Computer Graphics Resources

This is a curated list of computer graphics tutorials and resources.

- Formative papers in the field
- Introductory resources / tutorials
- Groundbreaking research / state-of-art techniques
- Software packages and tools

This document is a work in progress - some sections have received a lot less love than others and I intend to correct that.

Please suggest papers/articles/resources through [Github pull requests](https://help.github.com/articles/using-pull-requests/). If you believe this list is missing something or has factually inaccurate info, you can also file an issue in the [issue tracker](/issues).

## Contents

- [New to Graphics?](#start)
- [Other Collections](#collections)
- [Course Notes](#courses)
- [Textbooks](#textbooks)
- [Physically-based (Photorealistic) Rendering](#pbr)
  - [Overview and Survey](#pbr-survey)
  - [Ray Tracing](#rt)
  - [Vanilla Path Tracing](#pt)
  - [Photon Mapping](#pm)
  - [Bidirectional Path Tracing](#bpt)
  - [Metropolis Light Transport](#mlt)
  - [Importance Sampling](#is)
  - [BRDF/BSDF/BSSRDF](#bsdf)
  - [Volume Rendering](#vol)
  - [Light Field Capture](#lf)
  - [Microfacet Models](#mf)
  - [GPU](#gpu)
  - [Hybrid Strategies & Miscellaneous](#misc)
- [3D Games](#games)
- [Non-Photorealistic Rendering](#npr)
- [Shader Art](#demoscene)
- [Fluids and Simulation](#sim)
- [Differential Geometry](#geo)
- [Three Dimensional Displays](#3d-display)
- [Meshes](#mesh)
- [Image-based Editing and Reconstruction](#image)
- [Virtual Reality](#vr)

<a name="start" />
## New to Computer Graphics?

Computer Graphics (CG) is a subfield of Computer Science pertaining to "making images with computers".

Fruits of computer graphics:

|<img src="http://compass.xboxlive.com/assets/0f/eb/0feb7a56-f8c1-45e1-a412-a7edf8141f4e.jpg?n=Microsoft_Hololens_1200x630.jpg" />|<img src="http://www.grg.org/images/BrainWhiteMatter.jpg"/>|<img src="http://www.deskeng.com/de/wp-content/uploads/2014/06/Fig3_Dassault_driving_620.jpg"/>|<img src="http://cdn1.sciencefiction.com/wp-content/uploads/2015/05/Star-Wars-Jar-Jar-Binks-banner.png" />|
|-|-|-|-|
|Virtual Reality| Diffusion Tensor Imaging| Automotive Design | Star Wars |

CG is ubiquitous and highly interdisciplinary; producing just 5 seconds of a [Pixar film](http://www.imdb.com/title/tt2096673/) will utilize techniques from these areas of computer science and mathematics:

- Data Structures and Algorithms
- Numerical Optimization
- Hardware and Systems
- Distributed and High-Performance Computing
- Robotics
- Finite Element Methods
- Fluid Dynamics
- Machine Learning
- Differential Geometry
- Topology
- Statistics
- Optics
- Signal Processing
- Nuclear Fusion (!!)
- Trigonometry (!!)

Exciting stuff. But if you're just getting started, this list can be overwhelming! Where to begin?

1. Make sure you have an introductory background in basic programming, algorithms, and data structures (such as a semester-long introductory CS course). Brush up on your trigonometry (sines, cosines, triangles, projection of vectors and planes).

2. You can play with computer graphics in whatever language you are most comfortable with. [Processing](https://processing.org/) or [Three.js (JavaScript)](http://threejs.org/) are the most painless languages to get your hands dirty with graphics. If you come from an artistic background, many familiar tools (Maya, Photoshop, Houdini) have scripting interfaces that let you build things procedurally.

3. Spend some time learning tools for CG artists (e.g. Maya, Houdini, Photoshop, Blender, ZBrush). Play some [Halo 5](https://www.youtube.com/watch?v=b7itmX6WlI4) and admire how much geometry is in the scene. These will give you a strong intuition of the capabilities and limitations of real-time graphics.

4. Textbooks and notes from university-level graphics courses are a good resource for learning more math-heavy concepts like physically-based rendering and geometry processing.

5. Remember to have fun! There are no rules.

<a name="collections" />
## Other Collections

Many items in the list shown here were consolidated from other reading lists, maintained by people who know a lot more graphics than I do. Please check them out!

- [Cornell CS663 Reading List](http://www.cs.cornell.edu/courses/cs6630/2015fa/index.shtml#books)
- [Ke-Sen Huang's Website](kesen.realtimerendering.com)
- [extremeistan's realtime GI collection](https://extremeistan.wordpress.com/2014/05/11/realtime-global-illumination-techniques-collection/)
- [realtimerendering.com](http://www.realtimerendering.com/)
- [Generative Art Links at hvidtfeldts.net](http://blog.hvidtfeldts.net/index.php/generative-art-links/)

<a name="courses" />
## Course Notes

- [Stanford CS348b: Image Synthesis](http://candela.stanford.edu/cs348b/doku.php)
- [CS6630 Cornell University - Realistic Image Synthesis](http://www.cs.cornell.edu/courses/cs6630/2015fa/index.shtml)
- http://www.cs.cornell.edu/Courses/cs6630/2012sp/schedule.stm
- [CMU 15-462/662](http://15462.courses.cs.cmu.edu/fall2015/)

<a name="textbooks" />
## Textbooks

- [Principles of Digital Image Synthesis](http://www.realtimerendering.com/Principles_of_Digital_Image_Synthesis_v1.0.1.pdf)
  - Graphics pipelines, CUDA, path tracing are for today, but physics is forever.
- [Computer Graphics: Principles and Practice, 3rd Edition, (Hughes 2013)](http://cgpp.net/about.xml)
  - Authoritative computer graphics reference for students and practitioners. Well-written and expansive in both breadth and depth.
- [Physically Based Rendering: From Theory to Implementation, 2nd Edition (Pharr 2010)](http://www.pbrt.org/)
  - THE Rendering Book. It also [won an Academy Award at the Oscars!](https://www.youtube.com/watch?v=7d9juPsv1QU)
- [GPU Gems 3, by NVIDIA](http://http.developer.nvidia.com/GPUGems3/gpugems3_part01.html)

<a name="pbr" />
## Physically-based (Photorealistic) Rendering

|<img src="http://www.yiningkarlli.com/projects/takuarender/images/room.jpg" height="200px" />|<img src="http://cgimg.s3.amazonaws.com/t/g01/554901/1191193_orig.jpg" height="200px" />|<img src="http://www.studio-aiko.com/temp/classroom/daylight/classroom_daylight_cam05.jpg" height="200px" />
| ------------- | ------------- | - |
|[Takua Renderer](http://www.yiningkarlli.com/projects/takuarender/) by Karl Li| [The Pianist](http://lelatr.cgsociety.org/art/disney-zbrush-cartoon-maya-modeling-photoshop-texturing-mudbox-roger-3d-1191193), by Leticia Reinaldo|[Classroom Scene](http://staiko.cgsociety.org/art/classroom-3ds-makingof-max-scene-cg-after-cgi-effects-animation-3dmax-photoshop-3d-3-d-vray-studio-aiko-electronic-895769) by Meny Hilsenrad|

Since Jim Kajiya's 1986 paper on "The Rendering Equation", the vast majority of renderers compute images by simulating the physics of light transport in the scene. Within Physically-based Rendering (PBR), there are 2 open challenges: (1) Render as accurately as possible, and (2) Render as fast as possible

PBR is sometimes used interchangeably with "Global Illumination" in literature, since light scattering is coupled to the shading model. In the end, pictures are made by photons moving into a camera, and nothing more.

<a name="pbr-survey" />
### Overview and Surveys

- PBRT book (see above)
- [Robust Monte Carlo Methods for Light Transport Simulation](https://graphics.stanford.edu/papers/veach_thesis/). Eric Veach. PhD Thesis, Stanford University, 1997.
  - Nearly 20 years later, this monster thesis is *still* relevant when it comes to developing rendering algorithms. Introduces Monte Carlo rendering methods, multiple importance sampling, bidirectional path tracing, Metropolis Light Transport.
- [Analytic Methods for Simulated Light Transport](http://www.cs.virginia.edu/~gfx/Courses/2003/ImageSynthesis/papers/General%20Rendering%20Stuff/ArvoThesis.pdf). James Avro. PhD Thesis, Yale University, December 1995

<a name="rt" />
### Raytracing

Before physically-based rendering theory was developed, 3D rendering was mostly a big bag of tricks that was raytracing. However, raytracing is still widely used today in production films and games, so it's still important to understand.

- [Realistic Raytracing, by Zack Waters](http://web.cs.wpi.edu/~emmanuel/courses/cs563/write_ups/zackw/realistic_raytracing.html)

<a name="pt" />
### Vanilla Path Tracing

We want to estimate the path integral of irradiance arriving at the sensor (eye) in the scene. In a (basic) path tracer, we sample paths by tracing them from the eye into the scene. A sampled path has nonzero radiance if it eventually touches an emitter.

- [The Rendering Equation](http://www.dca.fee.unicamp.br/~leopini/DISCIPLINAS/IA725/ia725-12010/kajiya-SIG86-p143.pdf) James T. Kajiya. SIGGRAPH 1986.
- [Simple PathTracing by Inigo Quilez](http://www.iquilezles.org/www/articles/simplepathtracing/simplepathtracing.htm)
- [smallpt (pathtracer in 99 lines of code) by Kevin Beason](http://www.kevinbeason.com/smallpt/)
  - Check out the various ports and extensions at the bottom of the page!

<a name="pm" />
### Photon Mapping

Path tracers converge slowly if the light source is small. Instead, we trace paths from the light source into the scene, and store where photons land. Then, we can use a naive raytracer to simply "gather" these photons at render time. At the expense of extra storage, it's easy to do realtime dynamic viewpoints.

- [Global illumination using photon maps](https://sites.fas.harvard.edu/~cs278/papers/pmap.pdf). Jensen, H. W. Rendering Techniques 1996.
- [Photon Mapping by Zack Waters](http://web.cs.wpi.edu/~emmanuel/courses/cs563/write_ups/zackw/photon_mapping/PhotonMapping.html)

<a name="bpt" />
### Bidirectional Path Tracing

Basic idea: combine eye->light tracing and light->eye tracing to increase convergence speed and reduce noise.

- [Bidirectional Estimators for Light Transport](#) Veach & Guibas. Proceedings of EGRW 1994.
- [Mathematical Models and Monte Carlo Algorithms for Physically Based Rendering] Lafortune. PhD Thesis, Katholieke Universiteit Leuven, February 1996.

<a name="mlt" />
### Metropolis Light Transport

MCMC sampling for light paths.

- [Metropolis light transport](https://graphics.stanford.edu/papers/metro/metro.pdf) Veach & Guibas. SIGGRAPH 1997.
- [Mitsuba Renderer](www.mitsuba-renderer.org) MLT is notoriously difficult to implement.
- [Peter Kutz's BPT+MLT Blog](http://bptmlt.blogspot.com/)

<a name="radiosity" />
### Radiosity

Similar to photon mapping. Light paths from the light sources are constructed, and hits are converted into point lights (VPLs). Then do multiple passes of raytracing and accumulate contributions from these point lights.

- [Instant Radiosity](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.40.2213&rep=rep1&type=pdf) Keller, A. SIGGRAPH 1997.
  - [Cornell CS663 Presentation on the Paper ](http://www.cs.cornell.edu/courses/cs6630/2012sp/slides/Boyadzhiev-Matzen-InstantRadiosity.pdf)

<a name="is" />
### Importance Sampling

When doing Monte Carlo integration, samples with value 0 are wasted computation. Instead, we want to use what we know about the scene to only sample nonzero path integral samples. There are lots of options - we can importance sample in image-gradient-domain, the BSDF, and even the light field g=L(x) itself.

- [Importance Sampling for Production Rendering](http://www.igorsklyar.com/system/documents/papers/4/fiscourse.comp.pdf). Siggraph 2010.
- [Monte Carlo Techniques for Direct Lighting Calculations](http://www.cs.utah.edu/~shirley/papers/tog94.pdf) Shirley et al. ACM Transactions on Graphics 1996.
- [Optimally Combining Sampling Techniques for Monte Carlo Rendering](http://www.cs.jhu.edu/~misha/ReadingSeminar/Papers/Veach95.pdf) Veach & Guibas. SIGGRAPH 1995.
- [Gradient-domain metropolis light transport](https://mediatech.aalto.fi/publications/graphics/GMLT/lehtinen2013siggraph_paper.pdf). Lehtinen et al. ACM Transactions on Graphics 2013.
- [Gradient-domain Path Tracing](https://mediatech.aalto.fi/publications/graphics/GPT/). Kettunen et al 2015.
- [A Machine Learning Approach for Filtering Monte Carlo Noise](http://cvc.ucsb.edu/graphics/Papers/SIGGRAPH2015_LBF/). SIGGRAPH 2015.

<a name="bsdf" />
### BRDF/BSDF/BSSRDF

Different materials (metal, wood, skin, leggings) interact with light in different ways due to material properties and geometric differences at a microscopic level. Shading models attempt to capture these behaviors across different materials.

- Chapter 15 of "Principles of Digital Image Synthesis" (Morgan-Kaufman 1995)
- [Geometrical Considerations and Nomenclature for Reflectance. National Bureau of Standards](https://graphics.stanford.edu/courses/cs448-05-winter/papers/nicodemus-brdf-nist.pdf). Nicodemus et al. (U.S.) monograph, issued October 1977.
- [A microfacet-based BRDF generator](http://www.cs.utah.edu/~shirley/papers/facets.pdf). Ashikhmin and Shirley. SIGGRAPH 2000.
- [A precomputed polynomial representation for interactive BRDF editing with global illumination](https://cseweb.ucsd.edu/~ravir/brdfgi.pdf) Ben-Artzi et al. ACM Transactions on Graphics, 2008.
- [A Reflectance Model for Computer Graphics](http://inst.cs.berkeley.edu/~cs294-13/fa09/lectures/cookpaper.pdf). Cook & Torrance. Computer Graphics. 14(3), pp. 307-316. 1981.
  - Cook-Torrance BRDF model.
- [Theory for Off-specular Reflection from Roughened Surfaces](http://www.graphics.cornell.edu/~westin/pubs/TorranceSparrowJOSA1967.pdf). Torrance & Sparrow. Journal of the Optical Society of America 57:9 (1967).
    - Torrance-Sparrow shading model.
- [Models of Light Reflection for Computer Synthesized Pictures](https://design.osu.edu/carlson/history/PDFs/blinn-light.pdf) - James F. Blinn, SIGGRAPH 1977.
  - This paper reviews Torrance-Sparrow, Phong model, and proposes the [Blinn-Phong](https://en.wikipedia.org/wiki/Blinn%E2%80%93Phong_shading_model) shading model as a computationally efficient alternative.
- [Shadowing by Non-Gaussian Random Surfaces](http://dx.doi.org/10.1109/TAP.1980.1142437). Garry S. Brown, IEEE Transactions on Antennas and Propagaion (1980).
- [A data-driven reflectance model](http://csbio.unc.edu/mcmillan/pubs/sig03_matusik.pdf) Matusik et al. SIGGRAPH 2003.
- [Experimental analysis of BRDF models](http://people.csail.mit.edu/addy/research/brdf/). Ngan et al. Proceedings of the 2005 Eurographics Symposium on Rendering.
- [A model for anisotropic reflection](http://www.irisa.fr/prive/kadi/Lopez/p273-poulin.pdf). Poulin & Fournier. SIGGRAPH 1990.
- [Generalization of the Lambertian Model and Implications for Machine Vision](http://www1.cs.columbia.edu/CAVE/publications/pdfs/Nayar_IJCV95.pdf). Oren & Nayar. International Journal of Computer Vision 14:3 (1995).
  - Introduces the Oren-Nayar reflectance model.
- [Bidirectional Reflection Distribution Function of Thoroughly Pitted Surfaces](http://www1.cs.columbia.edu/CAVE/publications/pdfs/Koenderink_IJCV99.pdf). Koenderink et al. International Journal of Computer Vision 31 (1999).
  - BRDF of surfaces that are rough at both macro and micro scale.

<a name="vol" />
### Volume Rendering & Participating Media

- Chapter 12 (Energy Transport) of Principles of Digital Image Synthesis.
  - Easy explanation of the volume rendering equation from the ground up.
- [Volume Rendering Techniques](http://http.developer.nvidia.com/GPUGems/gpugems_ch39.html). Ikits et al. GPU Gems, Pearson Education, 2004.
- [A Survey on Participating Media Rendering Techniques](http://maverick.inria.fr/Publications/2005/CPPSS05/cerezo.pdf). Cerezo et al. Visual Computer, 2005
- [A Radiative Transfer Framework for Rendering Materials with Anisotropic Structure](http://www.cs.cornell.edu/projects/diffusion-sg10/)
  - Scattering models usually assume isotropic media. This paper presents a scattering model that supports anisotropic scattering (hair, cloth, skin).
  - Contains nice derivations of the standard isotropic case as well, for the diffusion approximation and the dipole BSSRDF.
- [Interactive multiple anisotropic scattering in clouds](http://www-ljk.imag.fr/Publications/Basilic/com.lmc.publi.PUBLI_Inproceedings@117681e94b6_1e9c7f4/clouds.pdf). Bouthors et al. Proceedings of I3D 2008.
- [Unifying points, beams, and paths in volumetric light transport simulation](http://www.cs.dartmouth.edu/~wjarosz/publications/krivanek14upbp.html). Křivánek et al. SIGGRAPH 2014.
  - The results are SUUUUPER beautiful
- [Scalable and Heterogeneous Rendering of Subsurface Scattering Materials](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.228.817&rep=rep1&type=pdf) Arbree. PhD Thesis, Cornell University, 2009.
  - Thesis on rendering translucent materials, derviation of dipole approximation.
- [Virtual ray lights for rendering scenes with participating media](http://cg.ivd.kit.edu/publications/p2012/VRL/VRL.pdf). Novak et al. 2012 SIGGRAPH 2012.
- [Ray tracing volume densities](http://gfx.cs.virginia.edu/courses/2003/ImageSynthesis/papers/Volume%20Rendering/Ray%20Tracing%20Volume%20Densities.pdf). Kajiya & von Herzen.SIGGRAPH 1984, July 1984.
- [Semi-Automatic Generation of Transfer Functions for Direct Volume Rendering](http://www.graphics.cornell.edu/pubs/1999/Kin99.pdf). Kindlmann & Durkin. IEEE Symposium on Volume Visualization 1998.
- [GigaVoxels: ray-guided streaming for efficient and detailed voxel rendering](http://dl.acm.org/citation.cfm?id=1507152). Crassin et al. I3D 2009.
- [Reflection from Layered Surfaces Due to Subsurface Scattering](https://cseweb.ucsd.edu/~ravir/6998/papers/p165-hanrahan.pdf). Hanrahan & Krueger. SIGGRAPH 1993.
- [Wave Propagation and Scattering in Random Media](http://www.sciencedirect.com/science/book/9780123747013). Akira Ishimaru. Chapter 7 in Wave Propagation and Scattering in Random Media, Volume 1. Academic Press, 1978.
- [A model for volume lighting and modeling](http://www.cs.utah.edu/~shirley/papers/volshade.pdf). Kniss et al. IEEE TVCG 9:2 (2003).
- [Fast Volume Rendering Using a Shear-Warp Factorization of the Viewing Transformation](https://graphics.stanford.edu/papers/shear/shearwarp.pdf). Lacroute & Levoy. SIGGRAPH 1994.
- [Efficient Simulation of Light Transport in Scene with Participating Media using Photon Maps](http://www.cs.otago.ac.nz/cosc455/p311-jensen.pdf). Jensen & Christensen. Proceedings of SIGGRAPH 98.
- [A Practical Model for Subsurface Light Transport](https://graphics.stanford.edu/papers/bssrdf/bssrdf.pdf). Jensen et all. Proceedings of ACM SIGGRAPH 2001.
- [A Rapid Hierarchical Rendering Technique for Translucent Materials](http://graphics.ucsd.edu/~henrik/papers/fast_bssrdf/fast_bssrdf.pdf). Jensen & Buhler. SIGGRAPH 2002.
- [Multidimensional Transfer Functions for Interactive Volume Rendering](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.92.502&rep=rep1&type=pdf). Kniss et al. IEEE TVGG 2002.
- [Practical Rendering of Multiple Scattering Effects in Participating Media](https://cseweb.ucsd.edu/~ravir/HRPIEG.pdf). Premoze et al. Rendering Techniques 2004: 15th Eurographics Workshop on Rendering.
- [Physically-based simulation of rainbows](http://www.cs.dartmouth.edu/~wjarosz/publications/sadeghi11physically.html). Sadeghi et al. ACM Transactions on Graphics, 31(1), (2012).

<a name="lf" />
### Light Capture

Much camera. Very science. Wow.

- [Paul Debevec's Home Page](http://www.pauldebevec.com/)
  - Lots of great publications, resources, and free HDRI maps!
- [Acquiring the reflectance field of a human face](http://www.pauldebevec.com/Research/LS/debevec-siggraph2000-high.pdf). Debevec et al. SIGGRAPH 2000.
- [A Dual Light Stage](http://gl.ict.usc.edu/Research/DLS/). Hawkins et al. Proceedings of EGSR 2005.
- [Fast bilateral filtering for the display of high-dynamic-range images](https://people.csail.mit.edu/fredo/PUBLI/Siggraph2002/DurandBilateral.pdf). Durand & Dorsey. SIGGRAPH 2002.
- [DISCO: acquisition of translucent objects](http://www.gris.informatik.tu-darmstadt.de/~mgoesele/download/Goesele-2004-DAT.pdf). Goesele et al. ACM Transactions on Graphics. 23(3), pp. 835-844, 2004.
- [The Lumigraph](http://research.microsoft.com/pubs/68168/Gortler-SG96.pdf). Gortler et al. Siggraph 1996.
- [Femto-Photography: Visualizing Photons in Motion at a
Trillion Frames Per Second](http://web.media.mit.edu/~raskar//trillionfps/). Raskar et al.
- [Gradient domain high dynamic range compression](http://ahtariev.ru/OLD/content/hdr_art/hdrc.pdf). Fattal et al. ACM SIGGRAPH 2002.

<a name="mf" />
### Microfacet Models

Typically used to render high-frequency spatial information, like the knitting of cloth or the imperfections of skin.

- [Microfacet Models for Refraction through Rough Surfaces](https://www.cs.cornell.edu/~srm/publications/EGSR07-btdf.pdf). Walter et al. Eurographics Symposium on Rendering 2007.

- [Building Volumetric Appearance Models of Fabric using Micro CT Imaging](https://www.cs.cornell.edu/~kb/publications/SIG11CT.pdf). Zhao et al. ACM Transactions on Graphics (SIGGRAPH 2011).
 - [Structure-aware Synthesis for Predictive Woven Fabric Appearance](http://www.cs.cornell.edu/projects/ctcloth/). Zhao eet al. SIGGRAPH 2012.
- [Efficient Rendering of Human Skin](http://www.eugenedeon.com/project/efficient-rendering-of-human-skin/). d'Eon et al. Eurographics Symposium on Rendering 2007.

<a name="gpu" />
### GPU

TLDR: GPUs make everything better. But they are hard to program.

- [Understanding the Efficiency of Ray Traversal on GPUs](http://www.tml.tkk.fi/~timo/publications/aila2009hpg_paper.pdf). Timo Aila and Samuli Laine. Proc. High-Performance Graphics 2009
  - [Kepler and Fermi architecture Addendum](http://research.nvidia.com/publication/understanding-efficiency-ray-traversal-gpus-kepler-and-fermi-addendum). NVIDIA Technical Report 2012.

<a name="misc" />
### Hybrid Strategies & Miscellaneous

Modern and proprietary commercial renderers probably implement a combination of techniques (like MLT + BPT + PT or MLT + Photon Mapping + Radiosity).

- [Energy Redistribution Path Tracing](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.63.5938&rep=rep1&type=pdf). Cline et al. 2005. ACM Transactions on Graphics (TOG), 24(3) (2005).
  - Combines MLT with basic path tracing.
  - [Implementation Details](https://www.cs.ubc.ca/~batty/projects/ERPT-report.pdf)
- [Lightcuts: a scalable approach to illumination](http://www.graphics.cornell.edu/~bjw/lightcuts.pdf) Walter et al. ACM Transactions on Graphics 2005.
  - Render time usually scales linearly with number of lights. This method provides sublinear scaling cost.
- [Sorted Deferred Shading for Production Path Tracing](https://disney-animation.s3.amazonaws.com/uploads/production/publication_asset/70/asset/Sorted_Deferred_Shading_For_Production_Path_Tracing.pdf). Eisenacher et al.  EGSR 2013.
  - One of the secret sauces in Disney's Hyperion Renderer: rays are sorted by direction to improve cache locality of scene traversal?
- [Light transport simulation with vertex connection and merging](http://iliyan.com/publications/VertexMerging). Georgiev et al. SIGGRAPH 2012.
- [Reconstructing the indirect light field for global illumination](http://groups.csail.mit.edu/graphics/ilfr/ilfr_preprint.pdf) Lehtinen et al. SIGGRAPH 2012.
- [Global illumination with radiance regression functions](http://renpr.org/project/ShadeBot.htm)  (SIGGAPH 2013)
  - Using neural networks to predict the indirect light field.
  - [video](https://vimeo.com/70734281)
- [Temporal light field reconstruction for rendering distribution effects](http://groups.csail.mit.edu/graphics/tlfr/). Lehtinen et al. SIGGRAPH 2011.

<a name="games" />
## 3D Games

See Ke-Sen Huang's paper collection of i3d papers ([Symposium on Interactive 3D Graphics and Games](http://kesen.realtimerendering.com/)).

- [Tutorial on Spherical Harmonics (2003)](http://www.research.scea.com/gdc2003/spherical-harmonic-lighting.pdf)
- [Interactive Display of Isosurfaces with Global Illumination](http://content.lib.utah.edu/utils/getfile/collection/uspace/id/640/filename/5290.pdf). Wyman et al. IEEE TVGG 2006.
- [John Carmack's Fast Inverse Square Root](https://en.wikipedia.org/wiki/Fast_inverse_square_root)

<a name="npr" />
## Non-photorealistic Rendering

|<img src="http://chrisoatley.com/wp-content/uploads/2013/02/PapermanFeature.jpg" height="120px" />|<img src="https://cynicritics.files.wordpress.com/2013/09/waking-life-800-75.jpg" height="120px" /> |<img src="http://i.imgur.com/sC50qNf.png" height="120px"/>|
|--|--|--|
|Paperman| Waking Life| Pixar 2013 |

- [Painterly Rendering for Animation](https://disney-animation.s3.amazonaws.com/uploads/production/publication_asset/47/asset/p477-meier_1996.pdf) Meier, Barbara. Disney Animation Research, 1996.
- [Stylizing Animation by Example](http://graphics.pixar.com/library/ByExampleStylization/paper.pdf). Pixar Animation. 2013.
- [Coherent Noise for Non-Photorealistic Rendering](http://graphics.pixar.com/library/NPRNoise/paper.pdf)

<a name="shaders" />
## Shader Art

Turns out you can do quite a lot of graphics using only a quad and an OpenGL fragment shader.

|<img src="http://blog.hvidtfeldts.net/media/pt2.jpg" height="200px" />|<img src="https://pbs.twimg.com/media/CWLz8htUsAAxQ-u.png:large" height="200px"/>|
|------|-----|
|[Path tracing fractals](http://blog.hvidtfeldts.net/index.php/2015/01/path-tracing-3d-fractals/) by Mikael Hvidtfeldt Christensen|[Arlo ... in a fragment shader](https://t.co/jJeGzTGmNC) by Inigo Quilez|

- [The Book of Shaders by Patricio Gonzalez Vivo](http://patriciogonzalezvivo.com/2015/thebookofshaders/)
   - The book appears to have been left unfinished, but what has been written so far is pretty good introductory material.
- [ShaderToy](http://shadertoy.com) A big collection of awesome fragment shaders. Many of these use cool tricks to do cheap lighting and imgae-space effects like blur/vignetting.
- [Articles by Inigo Quilez](http://www.iquilezles.org/www/index.htm)
- [Generative Art Links](http://blog.hvidtfeldts.net/index.php/generative-art-links/)

<a name="sim" />
## Fluids and Simulation

- [A material point method for snow simulation](https://www.math.ucla.edu/~jteran/papers/SSCTS13.pdf)
  - an outline of the techniques used in the snow simulation for Disney's Frozen. [video demo](https://www.youtube.com/watch?v=O0kyDKu8K-k)
  - Since the publication of this paper, Disney appears to invest quite heavily in MPM methods.
- [Augmented MPM for phase-change and varied materials
](https://disney-animation.s3.amazonaws.com/uploads/production/publication_asset/108/asset/siggraph2014_melt.pdf). Stomakhin et al. SIGGRAPH 2014.
- [Asynchronous Contact Mechanics](https://disney-animation.s3.amazonaws.com/uploads/production/publication_asset/10/asset/Asynchronous_Contact_Mechanics.pdf). Harmon et al. ACM communications 2012.
  - Another active area of research for Disney.

<a name="geo" />
## Differential Geometry

![diffgeom](http://brickisland.net/cs177fa12/wp-content/uploads/2012/10/ddg_differential.svg)

- [Keenan Crane's Homepage](http://www.cs.columbia.edu/~keenan/)
  - [Excellent Youtube Talk](https://www.youtube.com/watch?v=Mcal5Cy7r4E)
- [Globally Optimal Direction Fields](http://www.cs.columbia.edu/~keenan/Projects/GloballyOptimalDirectionFields/paper.pdf). Knöppel et al. SIGGRAPH 2014.

<a name="3d-display" />
## Three Dimensional Displays

Another dream of computer graphics:Iron-Man -styled Holograms.

|<img src="http://images.bwbx.io/cms/2012-08-07/0807_apple_630x420.jpg" height="200px" />|<img src="http://cdn2.gamefront.com/wp-content/uploads/2012/11/h4-17.jpg" height="200px" />|
|-|-|
|Iron Man 2|Halo|

- [Three-Dimensional Display Technologies: a Survey](https://www.osapublishing.org/aop/abstract.cfm?URI=aop-5-4-456). 2013.
- [Pixie Dust: Graphics Generated by Levitated and Animated Objects in Computational Acoustic-Potential Field](http://star.web.nitech.ac.jp/pdf/2014ToG.pdff)
- [Three Dimensional Images in the Air](http://www.aist.go.jp/aist_e/latest_research/2006/20060210/20060210.html)
  - TLDR: Focus laser beam, plasma emission phenomenon produces a burst of light at the focal point. Doing this at a high-enough frequency allows rasterization of plasma dots. Probably not safe to touch.

<a name="mesh" />
## Meshes

- [Mean Value Coordinates for Closed Triangular Meshes](http://www.cs.wustl.edu/~taoju/research/meanvalue.pdf). Ju, Schaefer, Warren. ACM Trans. on Graphics 2005.
- [Feature Adaptive GPU Rendering of Catmull-Clark Subdivision Surfaces](http://graphics.pixar.com/library/GPUSubdivRenderingA/paper.pdf)

<a name="image" />
## Image-based Editing and Reconstruction

- [Recovering high dynamic range radiance maps from photographs](http://www.pauldebevec.com/Research/HDR/debevec-siggraph97.pdf) Debevec & Malik 1997. In SIGGRAPH 97 (August 1997)
- [Accurate, Dense, and Robust Multi-View Stereopsis](http://www.di.ens.fr/sierra/pdfs/cvpr07a.pdf). Furukawa and Ponce 2010.
  - [Yasutaka Furukawa](http://www.cse.wustl.edu/~furukawa/)
- [Structure-aware Hair Capture](http://gfx.cs.princeton.edu/pubs/Luo_2013_SHC/). Luo, Li, Rusinkiewicz. Siggraph 2013.
- [Interactive digital photomontage](http://kneecap.cs.berkeley.edu/papers/photomontage/photomontage.pdf) Agarwala et al. ACM Trans. on Graphics, 23(3):294--302, Aug. 2004
- [Image-based reconstruction of spatial appearance and geometric detail](Image-based reconstruction of spatial appearance and geometric detail). Lensch et all. ACM Transactions on Graphics 2003.
- [Light field rendering](https://graphics.stanford.edu/papers/light/). Levoy & Hanrahan. Siggraph 1996.
- [Photo tourism: Exploring photo collections in 3D](http://phototour.cs.washington.edu/). Snavely, Seitz, Szzeliski. Siggraph 2006.
- [First Person Hyperlapse Videos](http://research.microsoft.com/en-us/um/redmond/projects/hyperlapse/) Microsoft Research 2014.
- [PatchMatch: A Randomized Correspondence Algorithm for Structural Image Editing](http://gfx.cs.princeton.edu/pubs/Barnes_2009_PAR/index.php). Barnes et al. Siggraph 2009.
- [Efficient Gradient-Domain Compositing Using Quadtrees](http://www.agarwala.org/efficient_gdc/preprint.pdf). ACM Trans. Graph. 2007

<a name="vr" />
## Virtual Reality

|<img src="http://o.aolcdn.com/hss/storage/midas/c0f52e59f1fee11b8834dc761b599598/202256278/microsoft-hololens-medical-studies.jpg" height="200px"/>|<img src="https://i.ytimg.com/vi/asduqdRizqs/maxresdefault.jpg" height="200px"/>
|-|-|
|Microsoft Hololens|Wow|

- [Oliver Kreylos's blog](http://doc-ok.org/) is a good resource to get started learning about VR / stereo rendering.
  - [Good Stereo vs. Bad Stereo](http://doc-ok.org/?p=77)
- [Implementing Stereoscopic 3D in your applications](http://www.nvidia.com/content/gtc-2010/pdfs/2010_gtc2010.pdf)
- [John Carmack's Oculus Connect 2015 talk](https://www.youtube.com/watch?v=Ti_3SqavXjkhttps://www.youtube.com/watch?v=Ti_3SqavXjk)
- [Why You Won’t See Hard AR Anytime Soon](http://blogs.valvesoftware.com/abrash/why-you-wont-see-hard-ar-anytime-soon/)
