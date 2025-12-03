# FanControl
A full installation of [Rem0o's FanControl](https://github.com/Rem0o/FanControl.Releases) package with my own PC's configuration.


# Configuration Overview

The case is a [Lian Li O11 Dynamic EVO](https://lian-li.com/product/o11-dynamic-evo/) with two sets of three [Lian Li UNI FAN AL V2](https://lian-li.com/product/uni-fan-al-v2/) fans mounted on the side and bottom as intake fans.

An [NZXT Kraken 360 RGB](https://nzxt.com/en-GB/product/kraken-360-rgb) AIO Liquid Cooler is provides both CPU cooling and acts as an overall exhaust.

The Lian Li case is configured in "reverse mode" meaning that the 3080 GPU's fans exhaust towards the top of the case approximately ~5 cm below the CPU radiator fans.


# FanControl Components
## Fans

### Main Fans
* ```Lian Li Uni Controller #1 Ch. 1 - Intake Side Fans```
* ```Lian Li Uni Controller #1 Ch. 2 - Intake Bottom Fans```
* ```NZXT Kraken - Exhaust Top Fans```
	* Control Curve: [```Main Fans - Mix```](#max-temperature---mix)

* ```NZXT Kraken - Pump```
  * Control Curve: [```CPU+AIO - Mix```](#cpuaio---mix)

* ```NVIDIA GeForce RTX 3080 - Outer Fans```
* ```NVIDIA GeForce RTX 3080 - Inner Fans```
  * Control Curve: ```Graphic Card 3080 - Auto```


## Main Fans - Mix

* [```CPU+AIO - Mix```](#cpuaio---mix)
* [```Motherboard Components - Max```](#motherboard-components---max)
* ```Graphic Card 3080 - Auto```
* ```DIMM - Mix```


## CPU+AIO - Mix

* ```AIO Liquid - Auto```
* ```CPU Core Average - Auto```


## Motherboard Components - Max

* ```PCH - Auto```


## DIMM - Mix
* ```DIMM#C01A1 - Auto```
* ```DIMM#C01A2 - Auto```
* ```DIMM#C01B1 - Auto```
* ```DIMM#C01B1 - Auto```

## Temperature Sensors

* [_NZXT Kraken_] ```AIO Liquid - Auto```
* ```Graphic Card 3080 - Auto```
* [_Motherboard Platform Hub Controller_] ```PCH - Auto```
* ```CPU Core Average - Auto```
* ```CPU Core Max - Auto```
* ```DIMM#C01A1 - Auto```
* ```DIMM#C01A2 - Auto```
* ```DIMM#C01B1 - Auto```
* ```DIMM#C01B1 - Auto```




# FanControl Logic
* All fans+pump should spin-up quickly but spin-down slowly
* All fans+pump have a minimum fan speed configured to maintain a minimal airflow.
* Intake & Exhaust fans are configured for a minimal positive pressure enviroment; when under load the system is strongly positive pressured with a good amount of heat passively exhausted to the rear of the case.
* The ```Max Temperature - Mix``` binds all the major heat sources and allows the [```Main Fans```](#main-fans) to exhaust the greatest heat load.

## Notes
* Lian Li fans appear to only be able to be commanded to run at >=1000 RPM eqv 20%, any lower and while the fans to spin down for a short time it's speculated some other process forces the fans to ~1000 RPM.
* NVIDIA GeForce RTX 3080 - Outer/Inner Fans stop spinning around 40%. The minimum is set to 45% as especially the inner fan has quite a hysteresis band to stop and start it. 

## Diagram
```
🌀 Main Fans (Mix)
├─ 🧩 Motherboard Components (Max)
│  └─ 📟 PCH (Auto)
├─ ❄️ CPU + AIO (Mix)
│  ├─ 💧 AIO Liquid (Auto)
│  └─ 🔥 CPU Core Average (Auto)
├─ 🎮 Graphic Card 3080 (Auto)
└─ 🧠 DIMM (Mix)
   ├─ 🔸 DIMM#C01A1 (Auto)
   ├─ 🔸 DIMM#C01A2 (Auto)
   ├─ 🔹 DIMM#C01B1 (Auto)
   └─ 🔹 DIMM#C01B1 (Auto)
```
