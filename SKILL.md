## Skill: manim-slides

### Description
Create presentation slide decks directly from Manim scripts using the **Manim‑Slides** plugin. The skill compiles a provided Manim scene (or multiple scenes) into a self‑contained HTML presentation (or optional PDF) that can be viewed in any browser.

### Input
- **manim_code** (string, required): A complete Manim script (or a snippet) that defines one or more `Slide` subclasses. The script should be compatible with the `manim-slides` plugin.
- **output_format** (enum, optional, default: `html`): Desired output format. Allowed values are:
  - `html` – interactive web presentation (default)
  - `pdf`  – static PDF export of the slides.
- **options** (object, optional): Additional configuration passed to the plugin. Common keys:
  - `theme` (string): Name of a built‑in or custom theme (e.g., `default`, `dark`).
  - `title` (string): Title displayed on the first slide.
  - `author` (string): Author name displayed in the footer.
  - `transition` (string): Transition style (`fade`, `slide`, `none`).
  - `output_path` (string): Absolute or relative path where the generated file should be saved. If omitted, a temporary file is created and its path returned.

### Output
- **output_path** (string): Path to the generated presentation file (`.html` or `.pdf`).
- **log** (string, optional): Any compilation warnings or messages from Manim.

### Example

**Note**: For generating basic Manim scripts, see the related skill `manim_basic.md` in this directory.

---

### Example
**Input**
```json
{
  "manim_code": """
from manim import *
from manim_slides import Slide

class IntroSlide(Slide):
    def construct(self):
        self.title("Manim Slides Demo")
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

**Output**
```json
{
  "output_path": "./output/intro_demo.html",
  "log": "Compilation succeeded in 2.3s"
}
```