# Manim Slides Skill

This repository provides **Pi‑compatible skills** for working with the **Manim‑Slides** plugin and basic Manim script generation. The skills are written in the standard `SKILL.md` format, making them consumable by any LLM that understands Pi skill definitions.

## Skills

| Skill            | File                          | Purpose                                                                                                                                                       |
| ---------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **manim‑slides** | `manim-slides/SKILL.md`       | Compile a Manim script (or snippets) into an interactive HTML presentation or a static PDF using the `manim‑slides` plugin.                                   |
| **manim‑basic**  | `manim-slides/manim_basic.md` | Generate a minimal Manim Python script that creates a scene with optional objects. Useful for quickly scaffolding animations before turning them into slides. |

Both skills follow the same structure:

```
## Skill: <skill‑name>

### Description
...

### Input
...

### Output
...

### Example
...
```

The **manim‑slides** skill includes a note linking to the basic Manim skill for convenience.

## Installation & Usage

1. **Clone the repository** (or copy the skill files into your Pi skill directory):
   ```bash
   git clone https://github.com/your‑username/manim‑slides‑skill.git
   ```
2. **Ensure the `manim-slides` plugin is installed** in the environment where you will run Manim:
   ```bash
   pip install manim-slides
   ```
3. **Load the skills in your Pi session** (Pi automatically discovers `SKILL.md` files under the current project directory).
4. **Invoke the skill** from an LLM prompt or via the Pi CLI, providing the required JSON input.

### Example: Create an HTML slide deck

```json
{
  "manim_code": """
from manim import *
from manim_slides import Slide

class IntroSlide(Slide):
    def construct(self):
        self.title('Manim Slides Demo')
        self.next_slide()
        self.play(Write(Text('Hello, world!')))
""",
  "output_format": "html",
  "options": {
    "theme": "dark",
    "title": "Demo Presentation",
    "author": "Alice Example",
    "transition": "fade"
  }
}
```

The skill returns a JSON object with the file path of the generated `intro_demo.html` and a compilation log.

### Example: Generate a simple Manim script

```json
{
  "objects": [
    { "type": "Text", "args": ["Hello Manim!"], "kwargs": { "font_size": 48 } },
    { "type": "Square", "kwargs": { "side_length": 2, "color": "BLUE" } }
  ],
  "duration": 3,
  "scene_name": "IntroScene"
}
```

The skill returns a ready‑to‑run Python file that can be rendered with:

```bash
manim -pql generated.py IntroScene
```

## Contributing

Feel free to open issues or submit pull requests to add more Manim‑related capabilities (e.g., animation helpers, custom slide transitions, or theme generation).

---

## License

MIT. See [LICENSE](LICENSE).

