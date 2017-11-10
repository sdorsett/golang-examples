# ensure glide is installed:
```
Stans-MacBook-Pro:helloworld standorsett$ which glide
/Users/standorsett/go/bin/glide
```
# glide init will create a glide.yaml file from the project directory you are in:
```
Stans-MacBook-Pro:helloworld standorsett$ glide init
[INFO]    Generating a YAML configuration file and guessing the dependencies
[INFO]    Attempting to import from other package managers (use --skip-import to skip)
[INFO]    Scanning code to look for dependencies
[INFO]    --> Found reference to golang.org/x/sys/unix
[INFO]    Writing configuration file (glide.yaml)
[INFO]    Would you like Glide to help you find ways to improve your glide.yaml configuration?
[INFO]    If you want to revisit this step you can use the config-wizard command at any time.
[INFO]    Yes (Y) or No (N)?
n
[INFO]    You can now edit the glide.yaml file. Consider:
[INFO]    --> Using versions and ranges. See https://glide.sh/docs/versions/
[INFO]    --> Adding additional metadata. See https://glide.sh/docs/glide.yaml/
[INFO]    --> Running the config-wizard command to improve the versions in your configuration
Stans-MacBook-Pro:helloworld standorsett$ cat glide.yaml
package: github.com/sdorsett/helloworld
import:
- package: golang.org/x/sys
  subpackages:
  - unix
```
# glide update will download any dependencies that are described in your project and store them in the vendor sub-directory:
```
Stans-MacBook-Pro:helloworld standorsett$ glide update
[INFO]    Downloading dependencies. Please wait...
[INFO]    --> Fetching golang.org/x/sys
[INFO]    Resolving imports
[INFO]    Downloading dependencies. Please wait...
[INFO]    Setting references for remaining imports
[INFO]    Exporting resolved dependencies...
[INFO]    --> Exporting golang.org/x/sys
[INFO]    Replacing existing vendor dependencies
[INFO]    Project relies on 1 dependencies.
```
# glide update will also create a glide.lock file that describes the version of the dependencies pulled down:
```
Stans-MacBook-Pro:helloworld standorsett$ ls -la
total 24
drwxr-xr-x  7 standorsett  staff  238 Nov 10 14:21 .
drwxr-xr-x  3 standorsett  staff  102 Nov 10 13:43 ..
drwxr-xr-x  3 standorsett  staff  102 Nov 10 13:43 cmd
-rw-r--r--  1 standorsett  staff  242 Nov 10 14:21 glide.lock
-rw-r--r--  1 standorsett  staff  100 Nov 10 14:20 glide.yaml
-rw-r--r--  1 standorsett  staff  242 Nov 10 14:19 helloworld.go
drwxr-xr-x  3 standorsett  staff  102 Nov 10 14:21 vendor

Stans-MacBook-Pro:helloworld standorsett$ cat glide.lock
hash: a3f44c8ef670983cba2b7e7cb525759ff9ba732a3ab1f4d5c28e47187e51e79a
updated: 2017-11-10T14:21:51.292774846-06:00
imports:
- name: golang.org/x/sys
  version: 1e2299c37cc91a509f1b12369872d27be0ce98a6
  subpackages:
  - unix
testImports: []

Stans-MacBook-Pro:helloworld standorsett$ tree vendor/
vendor/
└── golang.org
    └── x
        └── sys
            ├── AUTHORS
            ├── CONTRIBUTING.md
            ├── CONTRIBUTORS
            ├── LICENSE
            ├── PATENTS
            ├── README.md
            ├── codereview.cfg
            ├── plan9
            │   ├── asm.s
            │   ├── asm_plan9_386.s
            │   ├── asm_plan9_amd64.s
            │   ├── const_plan9.go
            │   ├── dir_plan9.go
            │   ├── env_plan9.go
            │   ├── env_unset.go
            │   ├── errors_plan9.go
            │   ├── mkall.sh
            │   ├── mkerrors.sh
            │   ├── mksyscall.pl
            │   ├── mksysnum_plan9.sh
            │   ├── pwd_go15_plan9.go
            │   ├── pwd_plan9.go
            │   ├── race.go
            │   ├── race0.go
            │   ├── str.go
            │   ├── syscall.go
            │   ├── syscall_plan9.go
            │   ├── syscall_test.go
            │   ├── zsyscall_plan9_386.go
            │   ├── zsyscall_plan9_amd64.go
            │   └── zsysnum_plan9.go
            ├── unix
            │   ├── README.md
            │   ├── asm_darwin_386.s
            │   ├── asm_darwin_amd64.s
            │   ├── asm_darwin_arm.s
            │   ├── asm_darwin_arm64.s
            │   ├── asm_dragonfly_amd64.s
            │   ├── asm_freebsd_386.s
            │   ├── asm_freebsd_amd64.s
            │   ├── asm_freebsd_arm.s
            │   ├── asm_linux_386.s
            │   ├── asm_linux_amd64.s
            │   ├── asm_linux_arm.s
            │   ├── asm_linux_arm64.s
            │   ├── asm_linux_mips64x.s
            │   ├── asm_linux_mipsx.s
            │   ├── asm_linux_ppc64x.s
            │   ├── asm_linux_s390x.s
            │   ├── asm_netbsd_386.s
            │   ├── asm_netbsd_amd64.s
            │   ├── asm_netbsd_arm.s
            │   ├── asm_openbsd_386.s
            │   ├── asm_openbsd_amd64.s
            │   ├── asm_openbsd_arm.s
            │   ├── asm_solaris_amd64.s
            │   ├── bluetooth_linux.go
            │   ├── cap_freebsd.go
            │   ├── constants.go
            │   ├── creds_test.go
            │   ├── dev_darwin.go
            │   ├── dev_darwin_test.go
            │   ├── dev_dragonfly.go
            │   ├── dev_dragonfly_test.go
            │   ├── dev_freebsd.go
            │   ├── dev_linux.go
            │   ├── dev_linux_test.go
            │   ├── dev_netbsd.go
            │   ├── dev_netbsd_test.go
            │   ├── dev_openbsd.go
            │   ├── dev_openbsd_test.go
            │   ├── dev_solaris_test.go
            │   ├── dirent.go
            │   ├── endian_big.go
            │   ├── endian_little.go
            │   ├── env_unix.go
            │   ├── env_unset.go
            │   ├── errors_freebsd_386.go
            │   ├── errors_freebsd_amd64.go
            │   ├── errors_freebsd_arm.go
            │   ├── export_test.go
            │   ├── flock.go
            │   ├── flock_linux_32bit.go
            │   ├── gccgo.go
            │   ├── gccgo_c.c
            │   ├── gccgo_linux_amd64.go
            │   ├── linux
            │   │   ├── Dockerfile
            │   │   ├── mkall.go
            │   │   ├── mksysnum.pl
            │   │   └── types.go
            │   ├── mkall.sh
            │   ├── mkerrors.sh
            │   ├── mkpost.go
            │   ├── mksyscall.pl
            │   ├── mksyscall_solaris.pl
            │   ├── mksysctl_openbsd.pl
            │   ├── mksysnum_darwin.pl
            │   ├── mksysnum_dragonfly.pl
            │   ├── mksysnum_freebsd.pl
            │   ├── mksysnum_netbsd.pl
            │   ├── mksysnum_openbsd.pl
            │   ├── mmap_unix_test.go
            │   ├── openbsd_pledge.go
            │   ├── openbsd_test.go
            │   ├── pagesize_unix.go
            │   ├── race.go
            │   ├── race0.go
            │   ├── sockcmsg_linux.go
            │   ├── sockcmsg_unix.go
            │   ├── str.go
            │   ├── syscall.go
            │   ├── syscall_bsd.go
            │   ├── syscall_bsd_test.go
            │   ├── syscall_darwin.go
            │   ├── syscall_darwin_386.go
            │   ├── syscall_darwin_amd64.go
            │   ├── syscall_darwin_arm.go
            │   ├── syscall_darwin_arm64.go
            │   ├── syscall_dragonfly.go
            │   ├── syscall_dragonfly_amd64.go
            │   ├── syscall_freebsd.go
            │   ├── syscall_freebsd_386.go
            │   ├── syscall_freebsd_amd64.go
            │   ├── syscall_freebsd_arm.go
            │   ├── syscall_freebsd_test.go
            │   ├── syscall_linux.go
            │   ├── syscall_linux_386.go
            │   ├── syscall_linux_amd64.go
            │   ├── syscall_linux_amd64_gc.go
            │   ├── syscall_linux_arm.go
            │   ├── syscall_linux_arm64.go
            │   ├── syscall_linux_mips64x.go
            │   ├── syscall_linux_mipsx.go
            │   ├── syscall_linux_ppc64x.go
            │   ├── syscall_linux_s390x.go
            │   ├── syscall_linux_sparc64.go
            │   ├── syscall_linux_test.go
            │   ├── syscall_netbsd.go
            │   ├── syscall_netbsd_386.go
            │   ├── syscall_netbsd_amd64.go
            │   ├── syscall_netbsd_arm.go
            │   ├── syscall_no_getwd.go
            │   ├── syscall_openbsd.go
            │   ├── syscall_openbsd_386.go
            │   ├── syscall_openbsd_amd64.go
            │   ├── syscall_openbsd_arm.go
            │   ├── syscall_solaris.go
            │   ├── syscall_solaris_amd64.go
            │   ├── syscall_solaris_test.go
            │   ├── syscall_test.go
            │   ├── syscall_unix.go
            │   ├── syscall_unix_gc.go
            │   ├── syscall_unix_test.go
            │   ├── timestruct.go
            │   ├── types_darwin.go
            │   ├── types_dragonfly.go
            │   ├── types_freebsd.go
            │   ├── types_netbsd.go
            │   ├── types_openbsd.go
            │   ├── types_solaris.go
            │   ├── zerrors_darwin_386.go
            │   ├── zerrors_darwin_amd64.go
            │   ├── zerrors_darwin_arm.go
            │   ├── zerrors_darwin_arm64.go
            │   ├── zerrors_dragonfly_amd64.go
            │   ├── zerrors_freebsd_386.go
            │   ├── zerrors_freebsd_amd64.go
            │   ├── zerrors_freebsd_arm.go
            │   ├── zerrors_linux_386.go
            │   ├── zerrors_linux_amd64.go
            │   ├── zerrors_linux_arm.go
            │   ├── zerrors_linux_arm64.go
            │   ├── zerrors_linux_mips.go
            │   ├── zerrors_linux_mips64.go
            │   ├── zerrors_linux_mips64le.go
            │   ├── zerrors_linux_mipsle.go
            │   ├── zerrors_linux_ppc64.go
            │   ├── zerrors_linux_ppc64le.go
            │   ├── zerrors_linux_s390x.go
            │   ├── zerrors_linux_sparc64.go
            │   ├── zerrors_netbsd_386.go
            │   ├── zerrors_netbsd_amd64.go
            │   ├── zerrors_netbsd_arm.go
            │   ├── zerrors_openbsd_386.go
            │   ├── zerrors_openbsd_amd64.go
            │   ├── zerrors_openbsd_arm.go
            │   ├── zerrors_solaris_amd64.go
            │   ├── zptrace386_linux.go
            │   ├── zptracearm_linux.go
            │   ├── zptracemips_linux.go
            │   ├── zptracemipsle_linux.go
            │   ├── zsyscall_darwin_386.go
            │   ├── zsyscall_darwin_amd64.go
            │   ├── zsyscall_darwin_arm.go
            │   ├── zsyscall_darwin_arm64.go
            │   ├── zsyscall_dragonfly_amd64.go
            │   ├── zsyscall_freebsd_386.go
            │   ├── zsyscall_freebsd_amd64.go
            │   ├── zsyscall_freebsd_arm.go
            │   ├── zsyscall_linux_386.go
            │   ├── zsyscall_linux_amd64.go
            │   ├── zsyscall_linux_arm.go
            │   ├── zsyscall_linux_arm64.go
            │   ├── zsyscall_linux_mips.go
            │   ├── zsyscall_linux_mips64.go
            │   ├── zsyscall_linux_mips64le.go
            │   ├── zsyscall_linux_mipsle.go
            │   ├── zsyscall_linux_ppc64.go
            │   ├── zsyscall_linux_ppc64le.go
            │   ├── zsyscall_linux_s390x.go
            │   ├── zsyscall_linux_sparc64.go
            │   ├── zsyscall_netbsd_386.go
            │   ├── zsyscall_netbsd_amd64.go
            │   ├── zsyscall_netbsd_arm.go
            │   ├── zsyscall_openbsd_386.go
            │   ├── zsyscall_openbsd_amd64.go
            │   ├── zsyscall_openbsd_arm.go
            │   ├── zsyscall_solaris_amd64.go
            │   ├── zsysctl_openbsd_386.go
            │   ├── zsysctl_openbsd_amd64.go
            │   ├── zsysctl_openbsd_arm.go
            │   ├── zsysnum_darwin_386.go
            │   ├── zsysnum_darwin_amd64.go
            │   ├── zsysnum_darwin_arm.go
            │   ├── zsysnum_darwin_arm64.go
            │   ├── zsysnum_dragonfly_amd64.go
            │   ├── zsysnum_freebsd_386.go
            │   ├── zsysnum_freebsd_amd64.go
            │   ├── zsysnum_freebsd_arm.go
            │   ├── zsysnum_linux_386.go
            │   ├── zsysnum_linux_amd64.go
            │   ├── zsysnum_linux_arm.go
            │   ├── zsysnum_linux_arm64.go
            │   ├── zsysnum_linux_mips.go
            │   ├── zsysnum_linux_mips64.go
            │   ├── zsysnum_linux_mips64le.go
            │   ├── zsysnum_linux_mipsle.go
            │   ├── zsysnum_linux_ppc64.go
            │   ├── zsysnum_linux_ppc64le.go
            │   ├── zsysnum_linux_s390x.go
            │   ├── zsysnum_linux_sparc64.go
            │   ├── zsysnum_netbsd_386.go
            │   ├── zsysnum_netbsd_amd64.go
            │   ├── zsysnum_netbsd_arm.go
            │   ├── zsysnum_openbsd_386.go
            │   ├── zsysnum_openbsd_amd64.go
            │   ├── zsysnum_openbsd_arm.go
            │   ├── zsysnum_solaris_amd64.go
            │   ├── ztypes_darwin_386.go
            │   ├── ztypes_darwin_amd64.go
            │   ├── ztypes_darwin_arm.go
            │   ├── ztypes_darwin_arm64.go
            │   ├── ztypes_dragonfly_amd64.go
            │   ├── ztypes_freebsd_386.go
            │   ├── ztypes_freebsd_amd64.go
            │   ├── ztypes_freebsd_arm.go
            │   ├── ztypes_linux_386.go
            │   ├── ztypes_linux_amd64.go
            │   ├── ztypes_linux_arm.go
            │   ├── ztypes_linux_arm64.go
            │   ├── ztypes_linux_mips.go
            │   ├── ztypes_linux_mips64.go
            │   ├── ztypes_linux_mips64le.go
            │   ├── ztypes_linux_mipsle.go
            │   ├── ztypes_linux_ppc64.go
            │   ├── ztypes_linux_ppc64le.go
            │   ├── ztypes_linux_s390x.go
            │   ├── ztypes_linux_sparc64.go
            │   ├── ztypes_netbsd_386.go
            │   ├── ztypes_netbsd_amd64.go
            │   ├── ztypes_netbsd_arm.go
            │   ├── ztypes_openbsd_386.go
            │   ├── ztypes_openbsd_amd64.go
            │   ├── ztypes_openbsd_arm.go
            │   └── ztypes_solaris_amd64.go
            └── windows
                ├── asm_windows_386.s
                ├── asm_windows_amd64.s
                ├── dll_windows.go
                ├── env_unset.go
                ├── env_windows.go
                ├── eventlog.go
                ├── exec_windows.go
                ├── memory_windows.go
                ├── mksyscall.go
                ├── race.go
                ├── race0.go
                ├── registry
                │   ├── export_test.go
                │   ├── key.go
                │   ├── mksyscall.go
                │   ├── registry_test.go
                │   ├── syscall.go
                │   ├── value.go
                │   └── zsyscall_windows.go
                ├── security_windows.go
                ├── service.go
                ├── str.go
                ├── svc
                │   ├── debug
                │   │   ├── log.go
                │   │   └── service.go
                │   ├── event.go
                │   ├── eventlog
                │   │   ├── install.go
                │   │   ├── log.go
                │   │   └── log_test.go
                │   ├── example
                │   │   ├── beep.go
                │   │   ├── install.go
                │   │   ├── main.go
                │   │   ├── manage.go
                │   │   └── service.go
                │   ├── go12.c
                │   ├── go12.go
                │   ├── go13.go
                │   ├── mgr
                │   │   ├── config.go
                │   │   ├── mgr.go
                │   │   ├── mgr_test.go
                │   │   └── service.go
                │   ├── security.go
                │   ├── service.go
                │   ├── svc_test.go
                │   ├── sys_386.s
                │   └── sys_amd64.s
                ├── syscall.go
                ├── syscall_test.go
                ├── syscall_windows.go
                ├── syscall_windows_test.go
                ├── types_windows.go
                ├── types_windows_386.go
                ├── types_windows_amd64.go
                └── zsyscall_windows.go

13 directories, 325 files
Stans-MacBook-Pro:helloworld standorsett$
```
