---
date : 2023-10-05T21:15:00+09:00
draft : false
title : Unity - スライダーで音量を調整する
categories :
    - Unity
description : Slider と AudioMixer クラス関数によって音量を調整する。
---

```csharp
public Slider musicSlider;
public Slider soundSlider;
public AudioMixer mixer;

private void Start()
{
    mixer.GetFloat("Music", out float bgmVolume);
    musicSlider.value = bgmVolume;
    mixer.GetFloat("Sound", out float soundVolume);
    soundSlider.value = soundVolume;
}

public void MusicMaster(float vol)
{
    vol = musicSlider.value;
    if (vol == -30f) vol = -80f;
    mixer.SetFloat("Music", vol);
}

public void SoundMaster(float vol)
{
    vol = soundSlider.value;
    if (vol == -30f) vol = -80f;
    mixer.SetFloat("Sound", vol);
}
```

最後にスライダーの最大値を０に設定し、最小値を-30に設定してください。
