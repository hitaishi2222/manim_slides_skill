## Skill: manim-basic

### Description
Generate a minimal **Manim** Python script that creates a scene with optional objects (e.g., `Text`, `Square`, `Circle`). This skill helps LLMs quickly scaffold a Manim animation without any slide‑specific features.

### Input
- **objects** (array of objects, optional): List of objects to add to the scene. Each object is an object with:
  - `type` (string, required): Manim class name (e.g., `Text`, `Square`, `Circle`).
  - `args` (array, optional): Positional arguments passed to the class constructor.
  - `kwargs` (object, optional): Keyword arguments passed to the class constructor.
- **duration** (number, optional, default: `2`): Total length of the scene in seconds (the `self.wait` at the end).
- **scene_name** (string, optional, default: `MyScene`): Name of the generated `Scene` subclass.

### Output
- **manim_code** (string): Complete Python script that can be saved as `example.py` and rendered with `manim -pql example.py MyScene`.

### Example
**Input**
```json
{
  "objects": [
    {"type": "Text", "args": ["Hello Manim!"], "kwargs": {"font_size": 48}},
    {"type": "Square", "kwargs": {"side_length": 2, "color": "BLUE"}}
  ],
  "duration": 3,
  "scene_name": "IntroScene"
}
```

**Output**
```json
{
  "manim_code": """
from manim import *

class IntroScene(Scene):
    def construct(self):
        txt = Text('Hello Manim!', font_size=48)
        sq = Square(side_length=2, color=BLUE)
        self.add(txt, sq)
        self.wait(3)
"""
}
```