[OpenGL_Object](https://www.khronos.org/opengl/wiki/OpenGL_Object)


# Object Create and Destruction
`void glGen*(GLsizei n, GLuint *objects);`
`void glDelete*(GLsizei n ,  ocnst GLuint *objects);`

# Deletion orphaning 
Calling glDelet* on an object does not guarantee the immediate destruction of that object's contents. maybe it is still "in use", after it is deleted.
"in use ":
* it is bound to a context. This is not necessarily the current one , sice deleting it will automatically unbind from the context that caused the deletion.
* It is attached to a container object.

# Object Usage
`void glBind*(GLenum target, GLuint object)`
# Object zero 
The GLuint value 0 is treated specially by OpenGL objects.
For most object types, object 0 is much like the NULL pointer: it is not an objects
For some objects , Object 0 represent a kind of "default object"
For Framebuffers, Object 0 represents the default Framebuffer.

# Object Sharing 

Normally , each context is entirely separate from the others;nothing done in one can affect the others.

Objects that contain references to other objects  cannot be shared , nor can Query Objects be shared .

# Objects types 
## regular objects
* Buffer Objects
* Query Objects :
* Renderbuffer Objects
* Sampler Objects
* Texture Objects
## container objects:
* Framebuffer Objects:
* Program Pipeline Objects
* Transform Feedback Objects
* Vertex Array Objects


to set the name for an object can use the following functiopns;
```
void glObjectLabel (GLenu identifier , GLuint name , GLsizei length, const char* label);

void glObjectPtrLabel(void *ptr, GLsizei length , const char* label);

```


To retrieve the name of an object , use `glGenObjectLabel` and `glGetObjectPtrLabel`


