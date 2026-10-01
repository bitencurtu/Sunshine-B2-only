<script setup>
import {ref} from 'vue'
import PlatformLayout from '../../PlatformLayout.vue'
import AdapterNameSelector from './audiovideo/AdapterNameSelector.vue'
import DisplayOutputSelector from './audiovideo/DisplayOutputSelector.vue'
import DisplayDeviceOptions from "./audiovideo/DisplayDeviceOptions.vue";
import DisplayModesSettings from "./audiovideo/DisplayModesSettings.vue";
import Checkbox from "../../Checkbox.vue";

const props = defineProps({
  platform: String,
  config: Object,
})

const config = ref(props.config)
</script>

<template>
  <div id="audio-video" class="config-page">
    <PlatformLayout :platform="platform">
      <template #windows>
        <div class="alert alert-info mb-3" role="alert">
          <strong>B2-only audio build.</strong> Audio is captured directly from the active Voicemeeter B2 recording endpoint.
          Audio Sink, Virtual Sink and Steam Streaming Speakers are disabled and ignored.
        </div>
      </template>
      <template #freebsd>
        <div class="mb-3">
          <label for="audio_sink" class="form-label">{{ $t('config.audio_sink') }}</label>
          <input type="text" class="form-control" id="audio_sink" v-model="config.audio_sink" />
        </div>
      </template>
      <template #linux>
        <div class="mb-3">
          <label for="audio_sink" class="form-label">{{ $t('config.audio_sink') }}</label>
          <input type="text" class="form-control" id="audio_sink" v-model="config.audio_sink" />
        </div>
      </template>
      <template #macos>
        <div class="mb-3">
          <label for="audio_sink" class="form-label">{{ $t('config.audio_sink') }}</label>
          <input type="text" class="form-control" id="audio_sink" v-model="config.audio_sink" />
        </div>
      </template>
    </PlatformLayout>

    <!-- Disable Audio -->
    <Checkbox class="mb-3"
              id="stream_audio"
              locale-prefix="config"
              v-model="config.stream_audio"
              default="true"
    ></Checkbox>

    <AdapterNameSelector
        :platform="platform"
        :config="config"
    />

    <DisplayOutputSelector
      :platform="platform"
      :config="config"
    />

    <DisplayDeviceOptions
      :platform="platform"
      :config="config"
    />

    <!-- Display Modes -->
    <DisplayModesSettings
        :platform="platform"
        :config="config"
    />

  </div>
</template>
