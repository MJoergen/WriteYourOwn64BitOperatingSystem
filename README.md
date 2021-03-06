# WriteYourOwn64BitOperatingSystem
A self-made minimal OS

This follows the video series
[here](https://www.youtube.com/watch?v=FkrpUaGThTQ).

# File list
```
.
├── buildenv
│   └── Dockerfile
├── Makefile
├── src
│   └── impl
│       └── x86_64
│           └── boot
│               ├── header.asm
│               └── main.asm
└── targets
    └── x86_64
        ├── iso
        │   └── boot
        │       └── grub
        │           └── grub.cfg
        └── linker.ld

10 directories, 6 files
```

# Prerequisites
```
sudo apt install docker docker-compose
sudo apt install qemu qemu-system-x86-64
```

# Setup docker environment
```
sudo docker build buildenv -t myos-buildenv
```

# Enter docker environment
```
sudo docker run --rm -it -v $PWD:/root/env myos-buildenv
```

# Build kernel
```
make build-x86_64
```

# Exit the docker environment
```
exit
```

# Start the OS
```
qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso
```

