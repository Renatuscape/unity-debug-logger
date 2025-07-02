# Unity Debug Logger
A tool that allows debug statements to write both to console and to file.

## Using in Projects:
In Unity's Package Manager window:

Click "+" → "Add package from git URL"
Enter: https://github.com/yourusername/your-unity-tools.git#v1.0.0

Each project gets its own Packages/manifest.json entry:

```
{
  "dependencies": {
    "com.yourname.devtools": "https://github.com/yourusername/your-unity-tools.git#v1.0.0"
  }
}
```

# Dev Instructions
### Tagging new versions
#### After committing your changes
* git tag v1.0.0
* git push origin v1.0.0

#### For updates
* git tag v1.1.0
* git push origin v1.1.0

### Runtime Folder
Purpose: Code that runs in the actual game/application
Contains:
* Your main classes (DebugTool.cs, PaginatedView.cs, etc.)
* MonoBehaviours, ScriptableObjects
* Utility classes used during gameplay
* Anything players will use in the built game

**Examples**
```
public class DebugTool : MonoBehaviour 
{
    public void LogMessage(string msg) { ... }
}
```

### Editor Folder
Purpose: Code that only runs inside Unity Editor (not in builds)
Contains:
* Custom inspectors
* Editor windows/tools
* Build scripts
* Anything that helps with development but isn't needed by players

**Examples**
```
[CustomEditor(typeof(DebugTool))]
public class DebugToolEditor : Editor 
{
    // Custom inspector UI
}
```