---
layout: custom-post
title: "Tom Miller's render loop, a revision"
date: 2006-10-08
categories: news
---

Tom Miller, Managed DirectX's father figure, has made several posts on the game loop or render loop for the managed environment. His lastest post on the subject was back in May 2005. I'm writing the render loop for Alien Sovereign using GDI+, so I needed to tweak his code a little to make it work for a non-DirectX renderer.

```csharp
using System;
using System.Runtime.InteropServices;
using System.Windows.Forms;

public static class Program
{
    [StructLayout(LayoutKind.Sequential)]
    public struct Message
    {
        public IntPtr hWnd;
        public uint msg;
        public IntPtr wParam;
        public IntPtr lParam;
        public uint time;
        public System.Drawing.Point p;
    }

    [System.Security.SuppressUnmanagedCodeSecurity] // We won't use this maliciously
    [DllImport("User32.dll", CharSet = CharSet.Auto)]
    public static extern bool PeekMessage(out Message msg, IntPtr hWnd, uint messageFilterMin, uint messageFilterMax, uint flags);

    [STAThread]
    static void Main()
    {
        // Initialize application
        Application.SetCompatibleTextRenderingDefault(false);
        
        // Create main form
        Form form = new Form();
        form.Show();
        
        // Hook into application idle event
        Application.Idle += delegate(object sender, EventArgs e)
        {
            while (IsApplicationIdle())
            {
                Update();
                Render();
            }
        };
        
        // Run the application
        Application.Run(form);
    }

    private static bool IsApplicationIdle()
    {
        Message msg;
        return !PeekMessage(out msg, IntPtr.Zero, 0, 0, 0);
    }

    private static void Update()
    {
        // Game logic update code goes here
        throw new NotImplementedException();
    }

    private static void Render()
    {
        // Rendering code goes here
        throw new NotImplementedException();
    }
}
```