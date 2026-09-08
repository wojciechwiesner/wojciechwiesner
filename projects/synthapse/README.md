# Synthapse & KKiK — Real-Time Frontier Generative AI Techno Studio

> Real-time generative AI techno performance instrument powered by Google Lyria with deterministic DSP audio watchdogs and physical Web MIDI hardware integration.

**Role:** Creator, Product Architect & Audio Systems Engineer  
**Live Demo:** [synthapse.theones.io](https://synthapse.theones.io) (surfaces: root, /play, /dj, /kkik)  
**Stack:** TypeScript · Google Lyria RealTime API · Web Audio API · WebGL Shaders · Meyda DSP · Web MIDI API · Vitest  
**Status:** Live interactive demo & production benchmark proving ground  

---

## 1. The Engineering Challenge

Generative audio foundation models (like Google Lyria or MusicLM) are capable of producing rich musical textures, but in real-time performance environments they suffer from fatal flaws:
1. **Spectral Drift & Mud:** Latent audio generation easily wanders in pitch, harmony, and rhythm over multi-minute sessions.
2. **Sub-Bass Phase Collisions:** In club sound systems, wide stereo low-end and overlapping kick transients create catastrophic acoustic phase cancellation and speaker distortion.
3. **Latency & Tactile Disconnect:** Touchscreens and mouse cursors lack the tactile velocity and muscle-memory feedback required for live electronic performance.

The system needed to harness generative audio while enforcing the uncompromising discipline of modern underground techno.

---

## 2. Architecture: Probabilistic Mood + Deterministic DSP

Synthapse uses a dual-engine architecture where **generative models create dynamic mood and texture, while deterministic DSP watchdogs guarantee pristine acoustic discipline**:

```text
Live Hardware Control (Akai MPD218 / MIDImix via Web MIDI)
                           ↓
             Synthapse Engine Core (State & Transport)
                           ↓
         ┌─────────────────────────────────┐
         │                                 │
         ▼                                 ▼
Google Lyria RealTime API        Local Web Audio DSP Chain
(Stems, ambiances, textures)      (Raw kicks, sidechain ducking, chops)
         │                                 │
         └────────────────┬────────────────┘
                          ↓
           Deterministic DSP Audio Watchdogs
   - Sub-bass mono collapse (<120Hz mono filter)
   - Real-time kick transient alignment
   - Meyda spectral flux & RMS monitoring
   - Zero-latency hard limiter & DC offset removal
                          ↓
               Clean Master Output (PA / Club)
```

### Key Technical Capabilities:
- **Zero-Latency Web Audio Engine:** Bespoke audio graph managing 40+ dynamic audio loops, vinyl stabs, percussion chops, and ducked sidechain compression without frame drops or audio pops.
- **Deterministic DSP Watchdogs:** A real-time audio analysis loop (Meyda DSP) continuously audits the frequency spectrum. Any sub-bass stereo widening is instantly collapsed to pure mono below 120Hz, ensuring punch and zero phase cancellation on big sound rigs.
- **Physical Web MIDI Integration:** Bi-directional hardware support for Akai MPD218 (16 velocity-sensitive backlit pads with bank switching) and Akai MIDImix (8 channel faders, 24 rotary knobs, LED status feedback), delivering true zero-latency physical stage control.
- **Boot Groove Invariant:** The instrument boots into a surgically clean, sparse groove (punchy kick + offbeat hi-hat + low-ducked dub stab). No automated noise risers, mid-range screeches, or clutter without explicit performer intent.

---

## 3. Empirical Benchmark Ground for JIT-Context OS

Synthapse served as the complex codebase for the scientific verification of **JIT-Context OS** (CERN Zenodo DOI: 10.5281/zenodo.22649542). 

In paired head-to-head autonomous engineering runs across 45 audio modules and 199 Vitest test suites:
- **2.44x Faster Task Delivery:** Cut wall-clock implementation time from 45.8 minutes to 18.8 minutes (-59%).
- **-61.4% LLM Turn Churn:** Reduced API round-trips from 171 to 66 turns.
- **Zero Error Loops:** 100% test pass rate on the first attempt with zero regression loops (vs 7 loops in the control arm).

---

*Live demo accessible at [synthapse.theones.io](https://synthapse.theones.io). Source code and internal audio engine proprietary.*
