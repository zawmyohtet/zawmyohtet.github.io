---
title: "My Quest for On-Device LLMs"
description: 'An Apple & Android Adventure!'
publishDate: 2025-06-23 15:45:46
language: 'English' 
tags: ['LLM', 'Gemma3', "GenAI"]
comment: false
---

Have you ever wondered what it would be like to run powerful language models right on your phone? I certainly did! So, when Apple announced their [Foundation Model Framework](https://developer.apple.com/documentation/foundationmodels) at this year's WWDC, my ears perked up immediately. I was captivated – how exactly would this work, and just how capable could it be?

The very next morning, I eagerly downloaded the Xcode beta, dove into their documentation, and set out to build some on-device LLM magic. My excitement hit a snag, though. Turns out, it couldn't run on the emulator, and upgrading my iPhone and Mac to the latest developer beta wasn't an option for me at the moment. Sigh – a minor setback!

Undeterred, my attention soon shifted to Android when I discovered their ML Kit GenAI API. I decided to try out their [Rewriting API](https://developers.google.com/ml-kit/genai/rewriting/android), only to face another hurdle: my Pixel 6a wasn't supported. Still, I was determined to see how convenient it would be to integrate ML Kit into an app. After a couple of hours (and a little help from Gemini for the UI!), I successfully integrated Android ML Kit into my app. While I finally got a taste of the developer experience, I was still itching for the actual user experience.

My story didn't end there! I had the incredible opportunity to attend Google I/O Extended Singapore 2025. One of the speakers gave a fantastic talk about on-device language models, and that's where I learned about the Google Gen AI Edge Gallery project. As soon as I got home, I compiled the app, and finally, I could experience on-device GenAI firsthand!

But my interest certainly didn't stop there. I decided to dig even deeper. Why not build something myself and truly get my hands dirty with the developer experience? This meant hours spent searching for the perfect model, grappling with the Android LLM Inference API, meticulously figuring out the UI, and dusting off my old Android development knowledge. So far, the UI is heavily inspired by the Google Gen AI Edge Gallery project and create the rewrite feature on my own way. I use [litert-community/Gemma3-1B-IT](https://huggingface.co/litert-community/Gemma3-1B-IT/tree/main) model. 

![Device](./screenshot_20250624_001128.png)

To Sum Up My On-Device LLM Journey:

- Both Android and iOS platforms good developer experience.
- Both Apple's Foundation Model Framework and Android's ML Kit APIs are quite user-friendly, though I believe the documentation could definitely be improved.
- If it works as expected on a wider range of devices, Apple's support for structured outputs and tool calling from their Foundation Model Framework will be a real game-changer.
- The Android LLM Inference API, in its current state, seems quite raw. Apps still need to load their own models, which might not be practical for widespread use and could ultimately lead back to relying on hosted LLM services.
- Gemma3 1B model can run on my Google Pixel 6a device pretty well. I haven't tried complicated task but the current result meet my expectation. (Hay! better don't expect too high on such small model, right?)

This is just the beginning of my exploration! I still have so much more to dig into, and I'm excited to share my new findings with you all soon!

> 𝘗𝘳𝘰𝘶𝘥𝘭𝘺 𝘮𝘺 𝘰𝘸𝘯 𝘵𝘩𝘰𝘶𝘨𝘩𝘵𝘴, 𝘴𝘩𝘢𝘳𝘱𝘦𝘯𝘦𝘥 𝘸𝘪𝘵𝘩 𝘵𝘩𝘦 𝘢𝘴𝘴𝘪𝘴𝘵𝘢𝘯𝘤𝘦 𝘰𝘧 𝘨𝘦𝘯𝘦𝘳𝘢𝘵𝘪𝘷𝘦 𝘈𝘐.