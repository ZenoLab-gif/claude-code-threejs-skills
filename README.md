# Three.js Skills for Claude Code

A curated collection of Agent Skills that help Claude Code build Three.js scenes, 3D interactions, shaders, loaders, lighting, post-processing, and animation with accurate API patterns.

This repository is a Claude Code oriented fork/adaptation of [CloudAI-X/threejs-skills](https://github.com/CloudAI-X/threejs-skills). The original work is MIT licensed; this fork keeps the same spirit and attribution while making the repository easier to install, discover, and maintain as a public Claude Code skills and plugin source.

## What This Provides

When working with Three.js, general coding agents often need precise details about current constructors, import paths, renderer setup, cleanup, performance tradeoffs, and how different Three.js systems fit together. These skills provide:

- Accurate Three.js API references and constructor signatures
- Working examples for common 3D web tasks
- Performance and cleanup guidance
- Cross-references between related Three.js systems
- Claude Code compatible `SKILL.md` frontmatter and descriptions

## Installation

### Install with a skills CLI

If you use an Agent Skills installer that supports GitHub repositories, install all skills from this repository:

```bash
npx skills add ZenoLab-gif/claude-code-threejs-skills
```

If your installer expects a full URL:

```bash
npx skills add https://github.com/ZenoLab-gif/claude-code-threejs-skills
```

To install a single skill:

```bash
npx skills add https://github.com/ZenoLab-gif/claude-code-threejs-skills --skill threejs-loaders
```

### Install as a Claude Code plugin

Claude Code plugin skills are namespaced by the plugin name. After installation, invoke skills as `/threejs-skills:threejs-fundamentals`, `/threejs-skills:threejs-loaders`, and so on.

Inside Claude Code:

```text
/plugin marketplace add ZenoLab-gif/claude-code-threejs-skills
/plugin install threejs-skills@claude-code-threejs-skills
```

Or with the Claude Code CLI:

```bash
claude plugin marketplace add ZenoLab-gif/claude-code-threejs-skills
claude plugin install threejs-skills@claude-code-threejs-skills
```

### Install for all Claude Code projects

Bash:

```bash
git clone https://github.com/ZenoLab-gif/claude-code-threejs-skills.git
mkdir -p ~/.claude/skills
cp -R claude-code-threejs-skills/skills/* ~/.claude/skills/
```

PowerShell:

```powershell
git clone https://github.com/ZenoLab-gif/claude-code-threejs-skills.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills"
Copy-Item -Recurse -Force ".\claude-code-threejs-skills\skills\*" "$HOME\.claude\skills\"
```

### Install for one project

Copy the skill folders into a project's `.claude/skills` directory:

```bash
mkdir -p .claude/skills
cp -R path/to/claude-code-threejs-skills/skills/* .claude/skills/
```

On Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force ".\.claude\skills"
Copy-Item -Recurse -Force "path\to\claude-code-threejs-skills\skills\*" ".\.claude\skills\"
```

This repository intentionally keeps the source skills under `skills/`. Claude Code loads them after they are installed or copied into `~/.claude/skills`, a project's `.claude/skills`, or a Claude Code plugin's `skills` directory.

## Skills Included

| Skill | Use when |
| --- | --- |
| `threejs-fundamentals` | Setting up scenes, cameras, renderers, Object3D hierarchy, coordinate systems, or transforms |
| `threejs-geometry` | Creating built-in shapes, BufferGeometry, custom geometry, or instanced meshes |
| `threejs-materials` | Styling meshes with PBR, basic, phong, standard, or shader materials |
| `threejs-lighting` | Adding lights, shadows, environment lighting, helpers, or IBL |
| `threejs-textures` | Working with texture types, UVs, environment maps, render targets, or texture optimization |
| `threejs-animation` | Creating keyframe animation, skeletal animation, morph targets, animation mixers, or procedural motion |
| `threejs-loaders` | Loading GLTF/GLB models, textures, HDR environments, Draco, KTX2, or other assets |
| `threejs-shaders` | Writing GLSL, ShaderMaterial, uniforms, vertex effects, fragment effects, or shader extensions |
| `threejs-postprocessing` | Using EffectComposer, bloom, DOF, color grading, custom passes, or screen effects |
| `threejs-interaction` | Handling raycasting, controls, pointer input, touch input, selection, or object picking |

## Usage Examples

Claude Code can load these skills automatically when your request matches a skill description. You can also invoke them directly after personal or project skill installation:

```text
/threejs-fundamentals Create a responsive Three.js scene with a rotating cube
/threejs-loaders Load a GLB model with Draco compression and play its animations
/threejs-shaders Create a fresnel rim-light shader material
/threejs-interaction Add raycast hover and click selection to meshes
```

When installed as a plugin, use the namespaced form:

```text
/threejs-skills:threejs-fundamentals Create a responsive Three.js scene with a rotating cube
/threejs-skills:threejs-loaders Load a GLB model with Draco compression and play its animations
/threejs-skills:threejs-shaders Create a fresnel rim-light shader material
/threejs-skills:threejs-interaction Add raycast hover and click selection to meshes
```

Natural-language requests work too:

- "Create a basic Three.js scene with a rotating cube."
- "Load a GLTF model with Draco compression and play its animations."
- "Add bloom post-processing and tune it for mobile performance."
- "Create a custom shader material with a fresnel effect."

## Repository Structure

Each skill is a folder containing a `SKILL.md` file:

```text
skills/
  threejs-fundamentals/
    SKILL.md
  threejs-loaders/
    SKILL.md
  threejs-shaders/
    SKILL.md
```

Each `SKILL.md` uses Agent Skills frontmatter:

```markdown
---
name: threejs-fundamentals
description: Three.js scene setup, cameras, renderer, Object3D hierarchy, coordinate systems. Use when setting up 3D scenes, creating cameras, configuring renderers, managing object hierarchies, or working with transforms.
---
```

The skill body then provides focused reference material, examples, common patterns, performance tips, and related skills.

## Verification

These skills are intended to align with modern Three.js documentation and patterns, including:

- Current `three/addons/` import paths
- Correct class names, constructor signatures, properties, and method names
- Renderer setup, resizing, animation-loop, cleanup, and disposal patterns
- Practical examples that can be adapted into Vite, React, Vue, vanilla JS, and other web projects

Before publishing changes, run static checks:

```bash
find skills -maxdepth 2 -name SKILL.md
```

Confirm every skill has valid frontmatter with a matching `name` and a useful `description`.

## Maintaining This Fork

This fork tracks the original project as upstream:

```bash
git remote add upstream https://github.com/CloudAI-X/threejs-skills.git
git fetch upstream
git merge upstream/main
```

When syncing, keep the public Claude Code installation instructions, attribution, and repository-specific URLs pointing to this fork unless intentionally upstreaming the changes.

## Contributing

Found an error or want to add coverage for additional Three.js features?

1. Fork this repository.
2. Edit or create skill files in `skills/<skill-name>/SKILL.md`.
3. Verify examples against the [Three.js documentation](https://threejs.org/docs/).
4. Open a pull request.

Skill guidelines:

- Use accurate, tested code examples.
- Keep descriptions specific so Claude Code can invoke the right skill.
- Avoid broad `allowed-tools` permissions unless there is a concrete reason.
- Document performance implications and cleanup requirements.
- Cross-reference related Three.js skills.

## License and Attribution

This fork is based on [CloudAI-X/threejs-skills](https://github.com/CloudAI-X/threejs-skills), which states MIT License terms. This adaptation preserves that attribution and remains MIT licensed.

Three.js is created and maintained by the [Three.js project](https://threejs.org/).
