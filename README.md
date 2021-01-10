# Wojciech's KBD75v1 keyboard configuration and settings tutorial

This is a short tutorial on getting your KBDFans KBD75 up and running.
I have revision 1 of this board, which I assembled myself from a kit.

Test your keyboard physical connections before proceeding.
I had 2 shorts around vias which made the keyboard matrix not work
correctly.
I encourage you to only start fiddling with firmware if your hardware works
fine.

Last note: if you are fine with default or semi-custom layouts and mappings,
it's probably much easier to do it through QMK's web-based configuration
tool: https://config.qmk.fm/#/

Of course, should you wish to proceed, you'll be able to retain full control
over your configuration.

# Quickstart

	brew update
	brew upgrade
	export PATH="/usr/local/opt/arm-gcc-bin@8/bin:$PATH"
	export PATH="/usr/local/opt/avr-gcc@8/bin:$PATH"
	export LDFLAGS="-L/usr/local/opt/avr-gcc@8/lib"
	mkdir wkoszek_kbd75v1 # pick your own directory name
	cd wkoszek_kbd75v1
	qmk setup -H `pwd`/qmk_firmware
	qmk config user.keyboard=kbdfans/kbd75/rev1

# Detailed explainer

I'm a macOS user. I had to upgrade my Xcode right away. Then:

	brew update
	brew upgrade

Then I put this in my `~/.bashrc`:

	export PATH="/usr/local/opt/arm-gcc-bin@8/bin:$PATH"
	export PATH="/usr/local/opt/avr-gcc@8/bin:$PATH"
	export LDFLAGS="-L/usr/local/opt/avr-gcc@8/lib"

Then:

	mkdir wkoszek_kbd75v1 # pick your own directory name
	cd wkoszek_kbd75v1
	qmk setup -H `pwd`/qmk_firmware

What you may end up seeing:

	$ qmk setup -H `pwd`/qmk_firmware
	Ψ Found qmk_firmware at /Users/wk/r/wkoszek_kbd75v1/qmk_firmware.
	Ψ QMK Doctor is checking your environment.
	Ψ Detected macOS.
	Ψ QMK home: /Users/wk/r/wkoszek_kbd75v1/qmk_firmware
	☒ Can't run `bin/qmk --version`

	Would you like to install dependencies? [Y/n] Y

You should accept. The tool will install all dependencies for you.
Running it 2nd time just proves everything works:

	$ qmk setup -H `pwd`/qmk_firmware
	Ψ Found qmk_firmware at /Users/wk/r/wkoszek_kbd75v1/qmk_firmware.
	Ψ QMK Doctor is checking your environment.
	Ψ Detected macOS.
	Ψ QMK home: /Users/wk/r/wkoszek_kbd75v1/qmk_firmware
	Ψ All dependencies are installed.
	Ψ Found arm-none-eabi-gcc version 8.3.1
	Ψ Found avr-gcc version 8.4.0
	Ψ Found avrdude version 6.3
	Ψ Found dfu-util version 0.10
	Ψ Found dfu-programmer version 0.7.2
	Ψ Submodules are up to date.
	Ψ QMK is ready to go

Then you're read to start building the default firmware:

	$ qmk compile -kb kbdfans/kbd75/rev1 -km default
	Ψ Compiling keymap with gmake kbdfans/kbd75/rev1:default


	QMK Firmware 0.11.38
	Making kbdfans/kbd75/rev1 with keymap default

	avr-gcc (Homebrew AVR GCC 8.4.0) 8.4.0
	Copyright (C) 2018 Free Software Foundation, Inc.
	This is free software; see the source for copying conditions.  There is NO
	warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

	Compiling: keyboards/kbdfans/kbd75/kbd75.c                                                          [OK]
	Compiling: keyboards/kbdfans/kbd75/rev1/rev1.c                                                      [OK]
	Compiling: keyboards/kbdfans/kbd75/keymaps/default/keymap.c                                         [OK]
	Compiling: quantum/quantum.c                                                                        [OK]
	Compiling: quantum/led.c                                                                            [OK]
	Compiling: quantum/keymap_common.c                                                                  [OK]
	Compiling: quantum/keycode_config.c                                                                 [OK]
	Compiling: quantum/matrix_common.c                                                                  [OK]
	Compiling: quantum/matrix.c                                                                         [OK]
	Compiling: quantum/debounce/sym_defer_g.c                                                           [OK]
	Compiling: quantum/color.c                                                                          [OK]
	Compiling: quantum/rgblight.c                                                                       [OK]
	Compiling: quantum/process_keycode/process_rgb.c                                                    [OK]
	Compiling: quantum/backlight/backlight.c                                                            [OK]
	Compiling: quantum/process_keycode/process_backlight.c                                              [OK]
	Compiling: quantum/backlight/backlight_driver_common.c                                              [OK]
	Compiling: quantum/backlight/backlight_avr.c                                                        [OK]
	Compiling: drivers/avr/ws2812.c                                                                     [OK]
	Compiling: quantum/led_tables.c                                                                     [OK]
	Compiling: quantum/process_keycode/process_space_cadet.c                                            [OK]
	Compiling: quantum/process_keycode/process_magic.c                                                  [OK]
	Compiling: quantum/process_keycode/process_grave_esc.c                                              [OK]
	Compiling: tmk_core/common/host.c                                                                   [OK]
	Compiling: tmk_core/common/keyboard.c                                                               [OK]
	Compiling: tmk_core/common/action.c                                                                 [OK]
	Compiling: tmk_core/common/action_tapping.c                                                         [OK]
	Compiling: tmk_core/common/action_macro.c                                                           [OK]
	Compiling: tmk_core/common/action_layer.c                                                           [OK]
	Compiling: tmk_core/common/action_util.c                                                            [OK]
	Compiling: tmk_core/common/print.c                                                                  [OK]
	Compiling: tmk_core/common/debug.c                                                                  [OK]
	Compiling: tmk_core/common/sendchar_null.c                                                          [OK]
	Compiling: tmk_core/common/util.c                                                                   [OK]
	Compiling: tmk_core/common/eeconfig.c                                                               [OK]
	Compiling: tmk_core/common/report.c                                                                 [OK]
	Compiling: tmk_core/common/avr/suspend.c                                                            [OK]
	Compiling: tmk_core/common/avr/timer.c                                                              [OK]
	Compiling: tmk_core/common/avr/bootloader.c                                                         [OK]
	Assembling: tmk_core/common/avr/xprintf.S                                                           [OK]
	Compiling: tmk_core/common/bootmagic.c                                                              [OK]
	Compiling: tmk_core/common/mousekey.c                                                               [OK]
	Compiling: tmk_core/protocol/lufa/lufa.c                                                            [OK]
	Compiling: tmk_core/protocol/usb_descriptor.c                                                       [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Class/Common/HIDParser.c                                       [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/Device_AVR8.c                                        [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/EndpointStream_AVR8.c                                [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/Endpoint_AVR8.c                                      [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/Host_AVR8.c                                          [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/PipeStream_AVR8.c                                    [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/Pipe_AVR8.c                                          [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/USBController_AVR8.c                                 [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/AVR8/USBInterrupt_AVR8.c                                  [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/ConfigDescriptors.c                                       [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/DeviceStandardReq.c                                       [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/Events.c                                                  [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/HostStandardReq.c                                         [OK]
	Compiling: lib/lufa/LUFA/Drivers/USB/Core/USBTask.c                                                 [OK]
	Linking: .build/kbdfans_kbd75_rev1_default.elf                                                      [OK]
	Creating load file for flashing: .build/kbdfans_kbd75_rev1_default.hex                              [OK]
	Copying kbdfans_kbd75_rev1_default.hex to qmk_firmware folder                                       [OK]
	Checking file size of kbdfans_kbd75_rev1_default.hex                                                [OK]
	 * The firmware size is fine - 22970/28672 (80%, 5702 bytes free)
