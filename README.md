# RocketSpectro

Team Rocket — Elektroniikan sovellusprojekti 2026 / Electronics Application Project 2026

---

# RocketSpectro

Team Rocket — Electronics Application Project 2026 / Elektroniikan sovellusprojekti 2026

---

## Projektin yleiskuvaus

RocketSpectro on reaaliaikainen audiospektrianalysaattori ja dB-mittari. Järjestelmä kaappaa audiota analogisesta mikrofonista ADC:n kautta, suorittaa 2048 pisteen FFT:n CMSIS-DSP-kirjastolla ja näyttää reaaliaikaisen taajuusspektrin palkkikaaviona sekä huippu-dB-mittarin 4,3 tuuman 800x480 RGB888 TFT-näytöllä.

---

## Project overview

RocketSpectro is a real-time audio spectrum analyzer and dB meter. It captures audio from an analog microphone via ADC, performs a 2048-point FFT using CMSIS-DSP, and displays a live frequency spectrum bar graph and peak dB meter on a 4.3" 800x480 RGB888 TFT display.

---

## Laitteisto

| Komponentti | Osanumero | Kuvaus |
|---|---|---|
| MCU | STM32H743ZIT6 | Pääsuoritin |
| Näyttö | DLC-T4.3CHR#2 | 4,3" 800x480 RGB888 TFT |
| SDRAM | W9825G6KH | 32 Mt ulkoinen muisti |
| Mikrofoni | Analoginen ADC:n kautta | Audiotallennus |
| Virransyöttö | USB-C 5V (vain virta) | Tehonsyöttö |
| Buck-muunnin | 3,3V | 3,3V käyttöjännite |
| Taustavaloajuri | MT3608 | Näytönvalaistus |

---

## Hardware

| Component | Part number | Description |
|---|---|---|
| MCU | STM32H743ZIT6 | Main processor |
| Display | DLC-T4.3CHR#2 | 4.3" 800x480 RGB888 TFT |
| SDRAM | W9825G6KH | 32 MB external memory |
| Microphone | Analog via ADC | Audio capture |
| Power input | USB-C 5V power only | Power supply |
| Buck converter | 3.3V rail | 3.3V supply rail |
| Backlight driver | MT3608 | Display backlight |

---

## Ohjelmistopino

| Kerros | Teknologia |
|---|---|
| Kehitysympäristö | STM32CubeIDE |
| Reaaliaikakäyttöjärjestelmä | FreeRTOS |
| Käyttöliittymäkirjasto | TouchGFX 4.x |
| DSP-kirjasto | CMSIS-DSP |
| Kielet | C ja C++ |

---

## Software stack

| Layer | Technology |
|---|---|
| IDE | STM32CubeIDE |
| RTOS | FreeRTOS |
| GUI framework | TouchGFX 4.x |
| DSP library | CMSIS-DSP |
| Languages | C and C++ |

---

## Järjestelmäarkkitehtuuri

Järjestelmä koostuu kolmesta FreeRTOS-taskista, jotka kommunikoivat keskenään FreeRTOS-jonojen kautta:

1. **AudioCaptureTask** — Kaappaa raakaa audiodataa ADC:ltä ja siirtää näytteet jonoon jatkokäsittelyä varten.
2. **FFTProcessingTask** — Vastaanottaa audionäytteitä jonosta, suorittaa 2048 pisteen FFT:n CMSIS-DSP-kirjastolla ja tuottaa taajuusspektridatan.
3. **UITask** — Lukee käsitellyt spektritiedot jonosta ja päivittää näytön reaaliaikaisen taajuusspektrin palkkikaavion ja huippu-dB-mittarin TouchGFX:n avulla.

Tiedonkulku: AudioCaptureTask -> jono -> FFTProcessingTask -> jono -> UITask

---

## System architecture

The system consists of three FreeRTOS tasks that communicate via FreeRTOS queues:

1. **AudioCaptureTask** — Captures raw audio data from the ADC and passes samples into a queue for further processing.
2. **FFTProcessingTask** — Receives audio samples from the queue, performs a 2048-point FFT using the CMSIS-DSP library, and produces frequency spectrum data.
3. **UITask** — Reads the processed spectrum data from a queue and updates the display with a live frequency spectrum bar graph and peak dB meter via TouchGFX.

Data flow: AudioCaptureTask -> queue -> FFTProcessingTask -> queue -> UITask

---

## Muistikartta

| Alue | Osoite | Koko | Kuvaus |
|---|---|---|---|
| SDRAM-kantaosoite | 0xD0000000 | 32 Mt | W9825G6KH |
| Kehyspuskuri | 0xD0000000 | 1 125 000 tavua | RGB888 800x480 |

---

## Memory map

| Region | Address | Size | Description |
|---|---|---|---|
| SDRAM base | 0xD0000000 | 32 MB | W9825G6KH |
| Framebuffer | 0xD0000000 | 1,125,000 bytes | RGB888 800x480 |

---

## Aloitus

1. Kloonaa repositorio ja avaa projektin kansio.
2. Avaa projekti STM32CubeIDE:ssä.
3. Generoi CubeMX-koodi (Project -> Generate Code).
4. Käännä projekti (Project -> Build All).
5. Ohjelmoi laite SWD-liitännän kautta (PA13/PA14/NRST).

---

## Getting started

1. Clone the repository and open the project directory.
2. Open the project in STM32CubeIDE.
3. Generate CubeMX code (Project -> Generate Code).
4. Build the project (Project -> Build All).
5. Flash the device via SWD (PA13/PA14/NRST).

---

## Repositorion rakenne

RocketSpectro/
  Core/
    Inc/
    Src/
  Drivers/
  Middlewares/
    FreeRTOS/
    TouchGFX/
  TouchGFX/
    App/
    Assets/
    generated/
    target/
  CMSIS-DSP/
  STM32CubeIDE/
  README.md

---

## Repository structure

RocketSpectro/
  Core/
    Inc/
    Src/
  Drivers/
  Middlewares/
    FreeRTOS/
    TouchGFX/
  TouchGFX/
    App/
    Assets/
    generated/
    target/
  CMSIS-DSP/
  STM32CubeIDE/
  README.md

---

## Tiimi

Valmistautukaa vaikeuksiin — ja tehkää siitä kaksinkertaista, sillä Team Rocket hoitaa homman.

| Jäsen | Rooli |
|---|---|
| Team Member 1 | Rooli |
| Team Member 2 | Rooli |
| Team Member 3 | Rooli |

---

## Team

Prepare for trouble — and make it double, because Team Rocket gets the job done.

| Member | Role |
|---|---|
| Team Member 1 | Role |
| Team Member 2 | Role |
| Team Member 3 | Role |

---

## Kurssitiedot

Elektroniikan sovellusprojekti 2026  
Oulun ammattikorkeakoulu (OAMK)

---

## Course information

Electronics Application Project 2026  
Oulu University of Applied Sciences (OAMK)
