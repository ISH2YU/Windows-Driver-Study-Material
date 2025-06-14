# Windows-Driver-Study-Material
Questionaire Study Material for Learning about Windows Driver basics and further how it can be exploited

# Questionnaire

#### Driver installation
- How to install and start a driver on the system using sc.exe.
- what changes happen in the registry on driver installation and startup?

#### Driver loading
- setup windbg for kernel debugging
- how to break debugger on driver load and try it.
- what does a driver object contain?
- how does a driver create a new device (when it is a software only driver/when it is a hardware driver)?
- how are the access rights of the device decided and what functions can driver use to create a device?
- what is sddl?
- where do most drivers create devices?

#### Interacting with drivers
- how to obtain a handle to a device created by a driver? (Remember you don't open a handle to a driver, you open handle to a device and requests to that device are routed to associated driver)
- what are dispatch routines in the driver object how can they be invoked given you have a handle to a device associated with that driver.
- what are IRPs. What kernel component creates them and how?
- how are parameters passed from user space to driver through IRP? (Think overlay and CurrentStackLocation)
- what are the 4 major ways in which input and output buffers of DeviceIoControl are passed into the kernel (TransferType). Briefly describe them.
- what is the CTL_CODE macro and how to identify the TransferType of the IOCTL code.
- what are device nodes, device stacks and driver stacks?
- using what function does a driver call another driver lower in the driver stack.
- what is FsContext and FsContext2 in the fileObject associated with the IRP. Give an example of how they are used in a common driver.

#### Advanced
- what are kernel pools and what are they used for. What are allocation tags?
- give a brief description of the kernel pool allocator.
- what is paged and non-paged memory?
- what is IRQL? why can't you sleep at IRQL >= 2? Why can't you access paged memory safely from IRQL >= 2?
- on x64 what concurrency primitives are present? Describe and explain the difference 
Between semaphores and mutexes.
- explain what is a refcount and how it can be used to prevent use-after-free. (Study how the object FSStreamReg in mskssrv has a refcount at ((DWORD*)FSStreamReg + 6), try to make it 0 without closing the file handle as a BONUS)
- explain what are reader-writer locks. Suggest how they can be implemented.
- when a class is instantiated in C++, how are it's methods maintained in the object?

#### Back to the user
- what are completion routines, how to register them in an IRP?
- what are DPCs? Give a few reasons why are they needed.

#### Bonus
- how does a kmdf driver differ from a wdm driver in terms of code?
- How do you reverse kmdf/wdf drivers? (Special reading: https://ioactive.com/wp-content/uploads/2018/09/Reverse_Engineering_and_Bug_Hunting_On_KMDF_Drivers.pdf)
- what are other types of drivers apart from wdm drivers with a brief description of a few
