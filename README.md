# android_kernel_samsung_smdk4412 (gd1wifi)

LineageOS 14.1 (Android 7.1.2) kernel for the **Samsung Galaxy Camera EK-GC110** (codename `gd1wifi`, Exynos 4412).

Forked from [LineageOS/android_kernel_samsung_smdk4412](https://github.com/LineageOS/android_kernel_samsung_smdk4412) (branch `cm-14.1`) with fixes specific to the Galaxy Camera hardware.

This is the first custom kernel / ROM ever built for this device, which shipped on Android 4.1.2 and was never officially updated.

---

## Key changes

**s6d6aa1 panel timing fix**
The i9300 base shipped the wrong porch values for this panel, causing severe display flicker. Corrected to the GC110's stock values in `arch/arm/mach-exynos/midas-lcd.c`:

- `h_fp = 60`
- `h_bp = 60`
- `v_fp = 36`
- `freq_limit = 51`

**Defconfig (`lineageos_gc1_defconfig`)**
Matched to real GC110 hardware:

- Correct PMIC: S5M8767 (`MFD_S5M_CORE`, `REGULATOR_S5M8767`)
- Correct magnetometer: `AK8963C`
- Camera ISP: `VIDEO_M9MO`
- Panel: `FB_S5P_S6D6AA1`
- Removed hardware the GC110 lacks: NFC, FM radio, various i9300 sensors

---

## Building

Built in-tree as part of a LineageOS 14.1 source tree with the matching device tree (`device/samsung/gc1`). Requires the cm-14.1 build environment (Java 8, Python 2 — a focal / 20.04 chroot works well on newer distros).

---

## License

GPLv2, inherited from the Linux kernel. See the [`COPYING`](COPYING) file for the full text.

---

## Credits

- LineageOS team & the smdk4412 maintainers
- **adamoutler** — original EK-GC100 kernel source
- **tubbohere & Treammc** — gd1wifi bring-up and s6d6aa1 panel fix
