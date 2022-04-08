# Laboratopy work 1 

## Decsription the libraries
1. **#include <GL/glew.h>** - (OpenGL Extension Wrangler Library) This is a cross-platform library for loading OpenGL extended functionality. When you initialize this library, it will check your platform and graphic card at run-time to know what functionality can be used in your program.
2. **#include <GL/freeglut.h>** -freeglut is an open source alternative to the OpenGL Utility Toolkit (GLUT). GLUT (and therefore freeglut) allows the user to create and manipulate windows that provide an OpenGL context on a wide range of platforms, as well as interact with the mouse, keyboard, and joystick. freeglut is meant to be a complete replacement for GLUT, and has very few differences from it. 
3. **#include <glm/vec3.hpp>** - Vec3 by glm is a utility class that represents a 3D vector
  
 ## Code Discription
 GLuint VBO;
 Vertex Buffer Object (VBO) is such an OpenGL facility that allows you to load certain data into GPU memory. For example, if you want to tell the GPU the coordinates of vertices, colors or normals, you need to create a VBO and put this data into it.

**glutInit(&argc, argv)**; options:int argc - number of arguments in the command line;  argv - is a pointer to an array of arguments (This values are taken from passed through entry point (int main(int argc, char** argv))). This is a GLUT initialization.

**glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA);**

*void glutInitDisplayMode(unsigned int mode)*;
The command has a single parameter, which can be represented by one of the following constants or a combination of these constants using a bitwise OR.

GLUT_RGB - 3 RGB color components are used to display graphics information.
GLUT_RGBA - Same as RGB but also uses 4 ALPHA (transparency) components.
GLUT_INDEX - The color is specified not with the help of RGB components, but with the help of a palette. Used for older displays where the number of colors is 256 for example.
GLUT_SINGLE - Output to the window is done using 1 buffer. Usually used for static information output.
GLUT_DOUBLE - Output to the window is done using 2 buffers. Used for animation to eliminate the flickering effect.
GLUT_ACCUM - Also use the Accumulation Buffer. This buffer is used to create special effects such as reflections and shadows.
GLUT_ALPHA - Use an ALPHA buffer. This buffer, as already mentioned, is used to set the 4th color component - ALPHA. Typically used for effects such as object transparency and anti-aliasing.
GLUT_DEPTH - Create a depth buffer. This buffer is used to clip hidden lines in 3D space when displayed on a flat screen monitor.
GLUT_STENCIL - The stencil buffer is used for effects such as cutting out part of a shape, making that part transparent. For example, by applying a rectangular stencil to the wall of a house, you will get a window through which you can see what is inside the house.
GLUT_STEREO - This flag is used to create stereo images. It is rarely used, since special equipment is needed to view such an image.

## Window Options
**glutInitWindowSize(1024, 768);** - *void glutInitWindowSize(int width, int height);* - The first parameter width is the window width in pixels, the second height is the window height in pixels.
**glutInitWindowPosition(100, 100);** - set the position of the created window relative to the upper left corner of the screen. This is done with the command: 
**glutCreateWindow("Tutorial 01");** - This command creates a window with the title you specify as a parameter and returns the window's HANDLER as an int. This HANDLER is typically used for subsequent operations on that window, such as changing window options and closing the window.
 ***Creating a window***
**glutCreateWindow("Tutorial 01");** - This command creates a window with the title you specify as a parameter and returns the window's HANDLER as an int. This HANDLER is typically used for subsequent operations on that window, such as changing window options and closing the window.

## Setting the functions responsible for drawing in the window and changing the shape of the window.
**glutDisplayFunc(RenderSceneCB);**
 void glutDisplayFunc(void (*func)(void));
After the window into which graphic information will be displayed or, as they say, graphic information is rendered, has been prepared and created, it is necessary to associate procedures with it that will be responsible for displaying graphic information, monitor window sizes, monitor keystrokes, etc. The very first and most necessary function that we will consider is responsible for drawing. It will always be called by the operating system to draw (redraw) the contents of the window. So, this function is set by the command:
The only parameter to this function is a pointer to a function that will be responsible for drawing to the window.

**glClearColor(1.0f, 1.0f, 1.0f, 1.0f);** 
 The first three arguments to this function set the red, green, and blue color components to 1.0. Thus, the white color of the image window is obtained. If instead of 1.0 we set the color of each component to
 

## Function for drawing a triangle
**glClear(GL_COLOR_BUFFER_BIT);** The glClear function clears buffers to preset values.
**GlutSwapBuffers();** displays the contents of the window on the screen, more precisely, it swaps the contents of the back and front buffers.

**The glGenBuffers procedure returns the specified number of currently unused VBO IDs.**
**glBindBuffer** binds a buffer object to the specified buffer binding point. Calling glBindBuffer with target set to one of the accepted symbolic constants and buffer set to the name of a buffer object binds that buffer object name to the target. If no buffer object with name buffer exists, one is created with that name. When a buffer object is bound to a target, the previous binding for that target is automatically broken.**
If glewInit() returns GLEW_OK, the initialization succeeded and you can use the available extensions as well as core OpenGL functionality. 

Function for clearing buffer(s) .

**void glDisableVertexAttribArray(0)**
**void glEnableVertexAttribArray(0)**
Specifies the index of the generic vertex attribute to be enabled or disabled.

 **void glVertexAttribPointer(GLuint index, GLint size, GLenum type, GLboolean normalized, GLsizei stride, const GLvoid * pointer)**
1) index specifies the index of the generic vertex attribute to be modified.
2)size specifies the number of components per generic vertex attribute. (1, 2, 3 or 4).
3)type specifies the data type of each component in the array (for example GL_BYTE, GL_INT).
normalized specifies whether fixed-point data values should be normalized (GL_TRUE) or converted directly as fixed-point values (GL_FALSE) when they are accessed.
stride specifies the byte offset between consecutive generic vertex attributes. If 0, the generic vertex attributes are understood to be tightly packed in the array. The initial value is 0.
4)pointer specifies a offset of the first component of the first generic vertex attribute in the array in the data store of the buffer currently bound to the GL_ARRAY_BUFFER target. The initial value is 0.
**void glDrawArrays(GLenum mode, GLint first, GLsizei count)** 
Finally, glDrawArrays is responsible for drawing primitives. The primitive type is passed as the first argument. In this case, a triangle is drawn. The second argument determines which vertex number to start at. The last argument specifies the number of vertices to use.

## Entering the main GLUT loop.
**glutMainLoop();

*void glutMainLoop(void);*
Well, the last thing to do in order to run our program is to enter the so-called main GLUT loop. This cycle launches the so-called heart of GLUT, which provides the relationship between the operating system and those functions that are responsible for the window, receive information from I / O devices. 
