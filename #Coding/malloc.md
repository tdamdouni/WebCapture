# malloc

_Captured: 2015-10-08 at 22:31 from [www.cplusplus.com](http://www.cplusplus.com/reference/cstdlib/malloc/)_

<cstdlib>

    
    void* malloc (size_t size);
    

Allocates a block of size bytes of memory, returning a pointer to the beginning of the block.

The content of the newly allocated block of memory is not initialized, remaining with indeterminate values.

If size is zero, the return value depends on the particular library implementation (it may or may not be a _null pointer_), but the returned pointer shall not be dereferenced.

### Parameters

size
    Size of the memory block, in bytes.  
[size_t](http://www.cplusplus.com/cstdlib:size_t) is an unsigned integral type.

### Return Value

On success, a pointer to the memory block allocated by the function.  
The type of this pointer is always `void*`, which can be cast to the desired type of data pointer in order to be dereferenceable.  
If the function failed to allocate the requested block of memory, a _null pointer_ is returned.

### Example

    
    
    /* malloc example: random string generator*/
    #include <stdio.h>      /* printf, scanf, NULL */
    #include <stdlib.h>     /* malloc, free, rand */
    
    int main ()
    {
      int i,n;
      char * buffer;
    
      printf ("How long do you want the string? ");
      scanf ("%d", &i);
    
      buffer = (char*) malloc (i+1);
      if (buffer==NULL) exit (1);
    
      for (n=0; n<i; n++)
        buffer[n]=rand()%26+'a';
      buffer[i]='\0';
    
      printf ("Random string: %s\n",buffer);
      free (buffer);
    
      return 0;
    }
    

[ Edit & Run](http://www.cplusplus.com/reference/cstdlib/malloc/)

This program generates a string of the length specified by the user and fills it with alphabetic characters. The possible length of this string is only limited by the amount of memory available to malloc

### Data races

Only the storage referenced by the returned pointer is modified. No other storage locations are accessed by the call.  
If the function reuses the same unit of storage released by a _deallocation function_ (such as [free](http://www.cplusplus.com/free) or [realloc](http://www.cplusplus.com/realloc)), the functions are synchronized in such a way that the deallocation happens entirely before the next allocation.

### Exceptions (C++)

**No-throw guarantee:** this function never throws exceptions.
