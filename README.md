# Biostage Studio (tablet)

A scientist's animation studio that combines **Animath** (Manim-style 2D: LaTeX maths, graphs, logic, nodes, geometry, stickers, drawing, values, camera, sound, Manim code export) with **Biostage** (3D: proteins from the PDB, molecules, lipid bilayers, tight junctions, paper stacks), plus new anatomy and cell-biology models. Everything sits on one CapCut-style timeline.

## Layout (iPad / tablet)
- **Menu bar:** File (new blank canvas, demos, projects, export), Edit, **Insert** (every category, plus Molecule by name, Protein by PDB ID, Search PDB), View.
- **Preview** in the middle. Drag an object to move it. Drag empty space to orbit the 3D world, and pinch or scroll to move the 3D camera closer.
- **Right panel**, always open. With something selected it shows Edit · Animate · Effects · Style · Keys · Rig, plus quick actions. With nothing selected it shows Layers · Scene · Camera · Values · Sound · Library · Code.
- **Timeline**, then the **tool dock**: Draw, Sketch, Text, Shapes, Graphs, Logic, Physics, Maths, Nodes, Geometry, 3D, Stickers, Media, Library, Values, Camera, Sounds, Scene, Code, Molecules, PDBs, Anatomy, Cell biology. Categories open a tray of things to add at the playhead.

## 3D objects
3D things are ordinary clips. They get Animath's entrance and exit animations (Create draws a protein along its chain or grows a membrane from the middle; Fade, Grow, Pop, Spin and the rest work too), keyframed position, scale and rotation, and parenting. The **3D** section of the Edit tab has their own keyable values, each with a ◇ key button, plus one-tap moves:
- **Protein:** cartoon, atoms, atom size, sticks, ligands. Includes Cartoon → atoms.
- **Molecule:** atom size, sticks. Find by name (PubChem 3D) or SMILES; about 50 common molecules also work offline.
- **Membrane:** curvature (flat → vesicle), jiggle, pore. **Tight junction:** gap, strands, leak.
- **Paper stack (PDF or image):** spread, fan, focus page, lift.
- **Bio models:** BBB capillary (cut-away), capillary, neuron (fire a signal), red blood cell, cell, mitochondrion, DNA (unzip), virus.
- **3D shapes:** sphere, cube, torus, knot and more, in glossy, matte, metal, glass, toon or wireframe.
- Every 3D object also has **Spin**, **Tilt** and **Depth**. The **Camera** tab has a keyable 3D camera (orbit, tilt, distance, lens) with Turntable and Dolly moves.

3D always draws behind the 2D layer, in one shared 3D space, so a protein can sit inside a membrane. Objects are fitted to a similar size unless you tick **True size** (1 unit = 10 Å).

## Sculpting and rigging (Clayframe)
3D → **Sculpt a clay head**, **Sculpt from scratch** or **Rigged clay character**, or a **puppet**: biped, quadruped, hexapod, octopod (spider) or octopod (octopus). Each puppet comes rigged and skinned with a looping two-second walk or swim cycle (also in Insert → Sculpt, and in Clayframe’s ⋯ menu) opens Clayframe full screen. It has sculpt brushes, objects, Rig (bones and skin weights), Pose, Stage (puppeteering with a controller or your face), shape keys and a timeline. **Use in scene** brings the result back as a clip that keeps its rig, shape keys and animation. The animation plays from the start of the clip, and you can set its speed and looping. **Edit in Clayframe** on a sculpt clip reopens the same Clayframe project, and **Update in scene** swaps the new version in.

## Labels that follow 3D
Any 2D object (text, maths, arrows, stickers, diagrams) can be **pinned to a 3D object or residue** from the **Pin to 3D** section of its Edit tab. It follows the object as the 3D camera moves, and its own position becomes an offset. An optional **leader line** grows in with the entrance animation. 3D objects have a **＋ Label pinned to it** button, and proteins and molecules also have **＋ Label a residue…**: tap a residue on the preview and the label takes its name.

## Transporters and channels
In Cell biology: **GLUT1**, **P-glycoprotein**, **aquaporin** and a **K⁺ ion channel**. Each carries its cargo across: glucose by alternating access, a drug pumped out with ATP, water in single file, and ions through an open gate. Speed, cargo and gate are all keyable. **Seat it in a membrane** puts the protein and a bilayer at the same true scale and opens a pore for it.

## Diffusion and data
- **Physics → Diffusion:** particles on a random walk, starting as a gradient, a drop or spread out, with an optional membrane barrier of adjustable permeability. Shows left/right counts and a live concentration profile.
- **Graphs → charts from CSV:** bar, line, scatter and **forest plots** (meta-analysis style, with a log scale, a line of no effect and a pooled diamond). Paste data or import a CSV file. Charts draw on with Create like any Manim object.

## Diagrams (2D, drawable with Create)
Neurovascular unit, capillary, brain, neuron, red blood cell, animal cell, mitochondrion, synapse, each with optional labels. **Hand over to 3D** crossfades a diagram into its matching 3D model (for example, the neurovascular unit becomes the BBB capillary).

Sculpts and 3D shapes can use a **clay** or **glazed clay** look (matcaps, as in Clayframe).

## Files
- `core.js`: Animath engine, with a small hook that draws the 3D layer.
- `sci2d.js`: diffusion and CSV charts (2D Animath types).
- `bio3d.js`: the 3D layer (three.js r128): structures, molecules, membranes, junctions, papers, bio models, 2D diagrams, PubChem and RCSB fetching.
- `editor.js`: the editor (Animath's, extended with the menu bar, dock trays, tablet panel, 3D inspector and gestures).
- `export.js`: Manim code export. 3D objects become placeholders.
- `clayframe/`: the Clayframe sculpt, rig and animate app (with an embed mode and a clay-head starter), opened by Studio in a full-screen frame.
- `app.css`, `index.html`, `fonts/`, `manifest.webmanifest`, `sw.js` (bump `VERSION` after changes).

## Notes
- Fetching from PubChem and the RCSB needs the internet. It works on GitHub Pages but not inside the Claude preview.
- Projects are stored in this browser, and structure files, PDFs and images in IndexedDB. File → Projects → Save project file carries them with it.
- Storage is separate from Animath's, so both apps can live on the same GitHub Pages site.
