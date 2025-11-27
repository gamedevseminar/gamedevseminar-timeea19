[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/LvIpavlS)
-----

# Lab 01: Unity Environment Setup

Welcome to Game Development\! 🎮

Your goal for Day 1 is to install the Unity Engine, set up your development environment, and prove that your code can talk to the Engine.

**⚠️ CRITICAL WARNING:** This repository comes with a specific `.gitignore` file. **DO NOT DELETE IT.** If you delete it, you will accidentally upload 5GB+ of temporary files and fail the assignment.

-----

## 📚 Part 1: Installation

Unity runs natively on Windows and macOS. You do NOT need a Virtual Machine.

### Step 1: Install Unity Hub

Download and install **Unity Hub** from the official site.

### Step 2: Install the Editor (LTS)

1.  Open Unity Hub.
2.  Go to **Installs** -\> **Install Editor**.
3.  Choose the latest **LTS (Long Term Support)** version (e.g., `2022.3.x` or `6000.x`).
      * *Do NOT choose a "Tech Stream" or "Beta".*
4.  **Important:** When asked for modules, check **"Microsoft Visual Studio Community"** (Windows) or verify you have **VS Code** (Mac). You need a script editor\!

-----

## 📝 Part 2: The Assignment

You will create a C\# script that asks the Unity Engine for its version and your computer's specs, then writes them to a file.

### Step 1: Open the Project

1.  Clone this repository to your computer.
2.  Open Unity Hub -\> **Projects** -\> **Add** -\> Select the folder you just cloned.
3.  Open the project (This may take a few minutes to import).

### Step 2: Create the Script

1.  In the **Project** window (bottom), right-click inside the `Assets` folder.
2.  Select **Create** -\> **C\# Script**.
3.  Name it exactly: `SystemCheck` (Case sensitive\!).
4.  Double-click to open it in your code editor.

### Step 3: The Code

Replace the default code with this:

```csharp
using UnityEngine;
using System.IO; 

public class SystemCheck : MonoBehaviour
{
    void Start()
    {
        // 1. Gather Data
        string content = "--- UNITY SETUP PROOF ---\n";
        content += $"Unity Version: {Application.unityVersion}\n";
        content += $"OS: {SystemInfo.operatingSystem}\n";
        content += $"Device: {SystemInfo.deviceName}\n";
        content += $"GPU: {SystemInfo.graphicsDeviceName}\n";
        content += "-------------------------";

        // 2. Write to file (Saved in the project root, next to Assets)
        string path = Path.Combine(Application.dataPath, "../proof.txt");
        File.WriteAllText(path, content);
        
        Debug.Log("✅ Proof generated at: " + path);
    }
}
```

### Step 4: Run It

A script does nothing unless it is in the scene.

1.  In the **Hierarchy** (left side), right-click -\> **Create Empty**. Name it `Bootstrapper`.
2.  Drag your `SystemCheck` script from the Project window onto the `Bootstrapper` object.
3.  Press the **Play Button** (▶) at the top.
4.  Watch the **Console** tab (bottom left). You should see: `"✅ Proof generated at: ..."`
5.  **Stop the game** (Press ▶ again).

-----

## 📸 Part 3: Verification & Submission

1.  **Check the File:** Go to your project folder. You should see `proof.txt` generated next to the `Assets` folder.
2.  **Screenshot:** Take a screenshot of your Unity Editor showing the **Console** with the success message. Save it as `screenshot.png` in your project folder.
3.  **Submit:**

<!-- end list -->

```bash
git add .
git commit -m "Lab 01 Setup Complete"
git push
```

### Checklist for Grading

  * [ ] `proof.txt` contains your Unity Version.
  * [ ] `screenshot.png` shows the Console output.
  * [ ] `SystemCheck.cs` is in the `Assets` folder.

-----

### 📺 Recommended Tutorial

[Unity Tutorial for Absolute Beginners [2025]](https://www.youtube.com/watch?v=AmGSEH7QcDg)

This video is relevant because it is a current (2025) walkthrough of the exact interface and "first script" workflow students will need to complete this specific assignment.
