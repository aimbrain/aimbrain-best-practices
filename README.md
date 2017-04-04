# Introduction

This document outlines the best practices of integrating the AimBrain SDKs. They help achieve the best results when using the AimBrain Biometric Authentication Platform.

# General

## Score interpretation

Each modality performs at it’s equal error rate when the threshold is set to “0.5”. This means when the threshold is set to 0.5, the false accept and false reject rates will be equal (e.g. 1% for the voice module).

In practical terms this means that the integration should start from using 0.5 as the acceptance threshold and modify it depending on the risk profile.

# Behavioural Module

## Data submission

The recommended way to submit behavioural data is to collecting at each activity/fragment/view and send it on activity/fragment/view change. This applies to any application such as mobile banking, trading, etc.

The timed periodical submission is designed for long running activities/fragments/views, for example document editing or chat applications.

## Sensitive views

It is recommended to make buttons such as the pin-code entry digits sensitive. This way the data sent is obfuscated and cannot be reconstructed into the original pin-code, while still providing important behavioural information on a frequently repeated task.

It is important to remember to register the elements made sensitive to ensure that the data is correct.

When making such views sensitive it is also important to remember to make any edit fields (if used) that track the data entry private, so the sensitive data isn’t accidentaly leaked through a different element.

# Face Module

We recommend using video for both enrolment and authentication.

## Enrolment

For best performance request the user to enrol 5 times, each time having a slightly different pose. We recommend the following:

1. Recording a video of the face straight
2. Recording a video slightly from the top
3. Recording a video slightly from the bottom
4. Recording a video slightly from the left
5. Recording a video slightly from the right

The video recording functionality of the SDK allows to set custom texts to advise the users of this procedure. See documentation for [Android](https://github.com/aimbrain/aimbrain-android-sdk#recording-video-of-users-face) and [iOS](https://github.com/aimbrain/aimbrain-ios-sdk#recording-video-of-the-users-face).

# Voice Module

## Enrolment

For best performance request the user to enrol 5 times. For a robust enrolment, we recommend generating the tokens for the process using the special [static tokentype values](https://aimbrain.github.io/aimbrain-api/#v1-voice-token).
