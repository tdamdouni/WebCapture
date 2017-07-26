# Determining the available amount of RAM on an iOS device

_Captured: 2016-05-22 at 17:46 from [stackoverflow.com](http://stackoverflow.com/questions/5012886/determining-the-available-amount-of-ram-on-an-ios-device/8540665#8540665)_


    #import <mach/mach.h>#import <mach/mach_host.h>void print_free_memory (){mach_port_t host_port;mach_msg_type_number_t host_size;vm_size_t pagesize;
    
        host_port = mach_host_self();
        host_size =sizeof(vm_statistics_data_t)/sizeof(integer_t);
        host_page_size(host_port,&pagesize);vm_statistics_data_t vm_stat;if(host_statistics(host_port, HOST_VM_INFO,(host_info_t)&vm_stat,&host_size)!= KERN_SUCCESS){NSLog(@"Failed to fetch vm statistics");}/* Stats in bytes */natural_t mem_used =(vm_stat.active_count +
                              vm_stat.inactive_count +
                              vm_stat.wire_count)* pagesize;natural_t mem_free = vm_stat.free_count * pagesize;natural_t mem_total = mem_used + mem_free;NSLog(@"used: %u free: %u total: %u", mem_used, mem_free, mem_total);}

Please note that this call does not account for memory that is being used by the gpu. If you are seeing a size that is smaller than expected system ram. It is more than likely allocated graphics memory.


## You can check the available RAM Memory in an iOS devices

    #import mach\mach.h
    #import mach\mach_host.h
     static natural_t get_free_memory(void)  
     {  
       mach_port_t host_port;  
       mach_msg_type_number_t host_size;  
       vm_size_t pagesize;  
       host_port = mach_host_self();  
       host_size = sizeof(vm_statistics_data_t) / sizeof(integer_t);  
       host_page_size(host_port, &pagesize);  
       vm_statistics_data_t vm_stat;  
       if (host_statistics(host_port, HOST_VM_INFO, (host_info_t)&vm_stat, &host_size) != KERN_SUCCESS)  
       {  
         NSLog(@"Failed to fetch vm statistics");  
         return 0;  
       }  
       /* Stats in bytes */  
       natural_t mem_free = vm_stat.free_count * pagesize;  
       return mem_free;  
     }  
