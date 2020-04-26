# FreeRTOS-Float-support-with-Newlib
The Integration of the Newlib support with FreeRTOS for the CubeMX generated STM32 projects


The intend of this tutorial is to add the Float, sprintf, snprintf and double printf support with the FreeRTOS

# The reason 
If you're using the FreeRTOS as middlewares then you might know that you need to allocate some amount of the stack to run the task seamlessly
The stack allocation may be static or dynamic 
Now when you need to print float and double or when you need to use snprintf and sprintf with FreeRTOS then that causes Hardwfault!

The reason behind this hard fault is nothing but stack overflow 

# Whats is the solution Solution?
The solution is to integrate the Newlib library with the porting file 
Newlib is a standard c library to use with the embedded system to emphasize the standard io with minimum footprint requirement 

# How to use it?

The porting is very simple!
(1) Replace the default heap_4.c file from the FreeRTOS middlewares with the heap_useNewlib.c 
That you can find at the directory, FreeRTOS/portable/Memmanage

(2) set to #define configUSE_NEWLIB_REENTRANT         1 in FreeRTOSConfig.h for the newlib support

(3)  Remember to configure "-u_printf_float" into the compiler 

Now you're ready to go 
Compile the entire solution and enjoy the float and double printf along with FreeRTOS without hardfault :)
