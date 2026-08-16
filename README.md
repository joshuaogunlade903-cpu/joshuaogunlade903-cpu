# Hey, I'm Joshua Ogunlade 👋🇳🇬

> *16-year-old software developer from Akure, Nigeria · Student at FUTA*

---

### 🚀 What I'm Building
**[Quart]

### The compiler behind Quart.
QTCC is the native compiler and toolchain for [Quart](#).It is designed to make systems programming feel direct without making developers manually manage the machinery underneath.
Write Quart. Let QTCC handle the rest.
```text
Quart source
↓
   QTCC
↓
 QTIR / QTUA
↓
 native machine code
↓
 FASM / object files
↓
LLD
↓
 executable / DLL
```
## Why QTCC?
Native development shouldn't require developers to become experts in their platform's entire build ecosystem.
QTCC's job is to understand the program and the target, then automatically handle the complicated parts of compilation and linking.
Instead of manually configuring:
* compilers
* assemblers
* linkers
* library paths
* object files
* platform-specific options
* DLL/shared-library configuration
* target-specific build settings
QTCC aims to make the toolchain itself responsible for those decisions.
```bash
quart build
```
That's the goal.
\## Built for Quart
QTCC is not a generic compiler frontend. It is being designed alongside the Quart language and its execution model.
Quart gives developers high-level abstractions when they want them while still allowing direct access to memory and platform functionality when they need it.
For example:
```quart
const a = 78
let b = 89
let ptr = @rawLoc(a)
let num = \*ptr
```
Or when you need to go all the way down to a platform API:
```quart
extern proc\[WriteFile\]:
\[win32x64=WriteFile\]:(usize, length, usize)
```
QTCC's responsibility is to make both levels work within the same toolchain.
## Cross-platform by design
QTCC is being built around the idea that **cross-platform development should not mean manually maintaining a pile of platform-specific build configurations.**
The compiler knows the target.
The compiler knows the architecture.
The compiler knows what the program requires.
It should therefore be able to select and configure the appropriate native toolchain automatically.
The long-term target is:
```text
Windows
Linux
Android
Web
```
with platform-specific machinery hidden behind the Quart toolchain wherever possible.
\## No build configuration maze
A new Quart project should not begin with a wall of configuration files.
The intended experience is closer to:
```text
my-project/
├── src/
└── libs/
```
Then:
```bash
quart init .
quart build
```
QTCC determines what is required and coordinates the compilation pipeline.
The goal isn't to remove control.
**The goal is to make control available when you want it instead of forcing it on you when you don't.**
## Low-level when you need it
QTCC doesn't try to prevent developers from reaching the machine.
Quart can work directly with:
* pointers
* raw memory
* external procedures
* native libraries
* platform APIs
* assembly
* object files
You can stay productive at the language level, or drop down into the machinery when your application actually requires it.
That makes QTCC suitable for the same kind of software where you'd normally reach for a systems language.
## The native toolchain
QTCC is designed to work with existing low-level tooling rather than reinventing every piece of the native toolchain.
For example:
```text
QTCC
  │
  ├── FASM
  │     └── assembly → object code
  │
  └── LLD
└── object files → final binary
```
This allows QTCC to focus on what it actually needs to own:
**understanding Quart and producing the correct native program.**
## Compiler architecture
QTCC is being developed around several compiler stages, including:
```text
Tokenizer
   ↓
Parser
   ↓
AST
   ↓
Lowering
   ↓
QTIR
   ↓
QTUA / backend
   ↓
Object generation
   ↓
Linking
```
The architecture is intentionally being developed so that platform-specific code generation does not leak throughout the entire compiler.
## Designed to grow
QTCC is not intended to stop at producing simple executables.
The toolchain is being built toward:
* native executables
* object files
* DLLs/shared libraries
* cross-platform compilation
* platform APIs through `extern`
* optimized release builds
* debugging support
* Quart's standard library
* future self-hosting
Eventually, QTCC itself can become a Quart program.
```text
QTCC
  ↓
compiles Quart
  ↓
Quart implementation of QTCC
  ↓
QTCC compiles itself
```
## Status
🚧 **QTCC is actively under development.**
The compiler is currently being developed alongside Quart, and major pieces of the native pipeline are still evolving.
Current work includes:
* [x] Core language compilation
* [x] Sizes u8 - u64
* [x] Sizes i8 - i64
* [ ] Sizes f32 and f64
* [x] Variables
* [x] Functions
* [x] Assembly Generation
* [ ] `if` `else`
* [ ] Pointer operations
* [x] `extern`
* [x] Object generation
* [x] DLL generation
* [ ] `.obj` generation
* [ ] Cross-platform toolchain
* [ ] Standard library
* [ ] Self-hosting
The architecture will continue to change as Quart matures.
## The philosophy
QTCC follows a simple idea:
> **The compiler should handle the machinery so the developer can focus on the program.**
You shouldn't need to understand five different build systems to compile a 200-line application.
You shouldn't need to manually hunt down incompatible dependencies.
You shouldn't need to configure machinery you didn't create just because you wanted to use it.
But when you **do** need the machinery, Quart should let you reach it.
That's QTCC.

### Part of the Quart ecosystem
QTCC is one component of the larger Quart ecosystem.
```text
QUART
│
┌───── ──┼─────────┐
│         │         │
QTCC      Yaki      QBot
Compiler   Renderer   Assistant
```
***Quart** — the programming language
**QTCC** — the compiler and native toolchain
***Yaki** — graphics and rendering infrastructure
***QBot** — the development assistant
The goal is a complete development environment where the language, compiler, tooling and runtime are designed to work together.

## Contributing
QTCC is being developed as an open project.
Compiler development, language design, backend work, optimization, tooling, documentation and testing are all welcome areas for contribution.
If you're interested in compilers, systems programming, language design or native toolchains, you're welcome here.
QTCC is being built from the ground up.
GitHub Link:
https://github.com/joshuaogunlade903-cpu/QTCC.git


**[Zenith.js](https://github.com/joshuaogunlade903-cpu/Zenith.js-release-)** — A full-stack JavaScript framework I built from scratch.

No build step. No npm install. No compiler. Drop a script tag and ship.

```html
<!-- This is all you need to start -->
<script src="zenith.js"></script>
```

```js
const { ZNative, DOM, Camera, Router, BindingManager } = Zenith

const app = new ZNative('div', {}, `
  <BoxHLayout spaceEvenly fillX>
    <TH1>Hello World</TH1>
    <PushButton _z_click="greet()">Click Me</PushButton>
  </BoxHLayout>
`)
app.runIn(DOM.body)
```

**What ships built-in:**
- 🗂 4-layer storage — FileSystem · Writer · FileManager · DataBase
- 🔁 Reactive binding — BindingManager · two-way state
- 🧵 Threading — Thread · SubProcess · Clock
- 📷 Camera — Camera · VideoRecorder · AudioRecorder · Microphone
- 🧭 Routing — Router · InternalRouter · RouteWrapper with auth guards
- 📋 Forms — FormValidator · FormHandle
- 🎨 Layout — BoxHLayout · BoxVLayout · GridLayout · StackLayout
- 🎬 Animation — zenithAnimate on every element
- 📄 Media — PDF · Video · Audio · WebView · Canvas as first-class tags
- 🔒 Types — Type · CN.Number · CN.String · runtime type enforcement

---

### 🛠 Tech I work with

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)

---

### 📊 Zenith Stats
<a href="https://zenith-gap.vercel.app">Zenith Vs The Big 3</a>
<a href="https://aboutzenith.vercel.app">Zenith Vs React Native</a>

---

### 📌 Featured Project

<a href="https://zenith-red-omega.vercel.app">Zenith.js</a>

---

### 💬 Motto

> **"Stop building bridges. Start building apps."**

---

### 📫 Reach me

- Instagram · Facebook — search **Joshua Ogunlade**
- GitHub issues on <a href="https://github.com/joshuaogunlade903-cpu/Zenith.js-release-">Zenith.js</a>
- WhatsApp <a href="https://chat.whatsapp.com/LFOXIbI5bsNGTKLKXN62Oi?mode=gi_t">Zenith Official Group</a>

---

*Built Zenith.js solo. Still in school. Just getting started.*
