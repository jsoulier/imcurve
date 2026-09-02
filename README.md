# ImCurve

Unreal-style curve editor and runtime using Dear ImGui

![](doc/image.png)

### Features and Controls

- Single and double precision curves
- Square, linear, and quadratic interpolation
- Automatically saved in imgui.ini
- Double LMB to add a point
- LCtrl+LMB to select a point
- LMB+drag to select or move points
- Delete to remove selected points
- RMB+drag to pan
- Mouse wheel to zoom
- RMB to change the interpolation type
- Ctrl+Z/R to undo and redo

### Example

```c++
#include <imgui.h>
#include <imcurve_editor.hpp>

class Character
{
public:
    Character()
        : Position{0.0f}
    {
    }

    void Update(float input, float dt)
    {
        float velocity = Velocity.GetCurve().Sample(input);
        Position += velocity * dt;
    }

    void RenderImGui()
    {
        Velocity.Draw("Velocity");
    }

private:
    ImCurveEditor<float> Velocity;
    float Position;
};
```
