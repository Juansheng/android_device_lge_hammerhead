# Notes on building AOSP
## Required components:
   * latest branch of hardware/qcom/msm8x74
   * latest Nexus 5 vendor blobs from Google, source tree looks like:
      
         ~/Pub/android/vendor$ tree
         .
         ├── broadcom
         │   └── hammerhead
         │       ├── BoardConfigPartial.mk
         │       ├── device-partial.mk
         │       └── proprietary
         │           ├── bcm2079x-b5_firmware.ncd
         │           ├── bcm2079x-b5_pre_firmware.ncd
         │           └── bcm4335c0.hcd
         ├── google
         │   └── hammerhead
         │       ├── BoardConfigPartial.mk
         │       ├── device-partial.mk
         │       └── proprietary
         │           ├── libgeofence.so
         │           ├── liblbs_core.so
         │           ├── librpmb.so
         │           ├── libssd.so
         │           ├── libthermalclient.so
         │           ├── libthermalioctl.so
         │           └── libwvm.so
         ├── lge
         │   └── hammerhead
         │       ├── BoardConfigPartial.mk
         │       ├── BoardConfigVendor.mk
         │       ├── device-partial.mk
         │       ├── device-vendor.mk
         │       └── proprietary
         │           ├── Android.mk
         │           ├── bu24205_LGIT_VER_2_DATA1.bin
         │           ├── ...
         │           └── vss_init
         └── qcom
             └── hammerhead
                 ├── BoardConfigPartial.mk
                 ├── device-partial.mk
                 └── proprietary
                     ├── a330_pfp.fw
                     ├── a330_pm4.fw
                     ├── adsp.b00
                     ├── ...
                     └── venus.mdt

## Required changes:
   * bionic: allow to link libraries that have text relocation sections
   * build: remove AOSP stock recovery if you like
   * hardware/qcom/{audio,bt,display,keymaster,gps,media}:

     revert Google changes on unsupported msm8974, commits follow as:

         Revert "msm8974: remove from top level makefile"
         Revert "msm8974: deprecate msm8974"

     Btw, why Google did this? To keep source clean? Sarcasm? :-|
   * kernel: SELinux patches

## Have fun.
