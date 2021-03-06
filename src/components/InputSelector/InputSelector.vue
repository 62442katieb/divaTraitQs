<template>
  <div class="inputContent">
    <div class="lead scroll mb-3 pr-3 pl-3" v-if="preamble">
      <p :class="{'text-justify': inputType==='audioPassageRecord'}">{{ preamble }}</p>
    </div>
    <div class="lead scroll mb-3 pr-3 pl-3" v-if="title">
      <p :class="{'text-justify': inputType==='audioPassageRecord'}">{{ title }}</p>
      <span v-if="valueConstraints.requiredValue" class="text-danger">*</span>
    </div>

    <b-alert variant="danger" show v-else>
      This item does not have a title defined
    </b-alert>

    <!-- If type is radio -->
    <div v-if="inputType==='radio'">
        <Radio
          :constraints="valueConstraints"
          :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is audioAutoRecord -->
    <div v-else-if="inputType==='audioAutoRecord'">
      <AudioCheckRecord
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is audioRecord -->
    <div v-else-if="inputType==='audioRecord'">
        <AudioRecord
          :constraints="valueConstraints"
          :selected_language="selected_language"
          :init="init" v-on:valueChanged="sendData"/>
    </div>

    <div v-else-if="inputType==='audioPassageRecord'">
      <AudioRecord
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is audioImageRecord -->
    <div v-else-if="inputType==='audioImageRecord'">
        <AudioRecord
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"
        mode="audioImageRecord" />
    </div>

    <!-- If type is audioRecordNumberTask -->
    <div v-else-if="inputType==='audioRecordNumberTask'">
      <AudioRecord
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"
        mode="audioRecordNumberTask" />
    </div>

    <!-- If type is text -->
    <div v-else-if="inputType==='text'">
        <TextInput
          :constraints="valueConstraints"
          :selected_language="selected_language"
          :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is time rnage -->
    <div v-else-if="inputType==='timeRange'">
        <TimeRange
          :constraints="valueConstraints"
          :selected_language="selected_language"
          :id="'timeRange' + Math.floor(Math.random()*1000)"
          :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is text -->
    <div v-else-if="inputType==='multitext'">
      <MultiTextInput :constraints="valueConstraints" :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is number -->
    <div v-else-if="inputType==='number'">
        <IntegerInput
          :constraints="valueConstraints"
          :selected_language="selected_language"
          :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is date -->
    <div v-else-if="inputType==='date'">
        <DateInput
          :constraints="valueConstraints"
          :selected_language="selected_language"
          :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is document upload -->
    <div v-else-if="inputType==='documentUpload'">
      <DocumentUpload
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is document upload -->
    <div v-else-if="inputType==='slider'">
      <SliderInput
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- If type is select input -->
    <div v-else-if="inputType==='selectCountry' || inputType === 'selectState'
      || inputType === 'selectLanguage' || inputType === 'select'">
      <SelectInput
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :inputType="inputType"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <div v-else-if="inputType ==='static' && readOnly">
      <StaticReadOnly
        :constraints="valueConstraints"
        :selected_language="selected_language"
        :result="true"
        :init="init" v-on:valueChanged="sendData"/>
    </div>

    <!-- if we don't have a component built for this type, then show an error -->
    <div v-else>
      <b-alert show>
        no input type UI built for "{{inputType}}" yet!
      </b-alert>
    </div>

    <!-- you can skip this question if requiredValue is not true -->
    <div class="row float-right" v-if="showPassOptions !== null ">
      <b-button class="" variant="default" v-if="showPassOptions['dontKnow']"
                @click="dontKnow">
        Don't Know
      </b-button>
      <b-button class="" variant="default" v-if="showPassOptions['skip']" @click="skip">
        Skip
      </b-button>
    </div>

  </div>
</template>

<script>
import Radio from '../Inputs/WebRadio/';
import AudioRecord from '../Inputs/WebAudioRecord/';
import TextInput from '../Inputs/WebTextInput/';
import IntegerInput from '../Inputs/WebIntegerInput/';
import DateInput from '../Inputs/YearInput/';
import MultiPart from '../MultiPart/';
import DocumentUpload from '../Inputs/DocumentUpload';
import MultiTextInput from '../Inputs/MultiTextInput';
import SliderInput from '../Inputs/SliderInput';
import TimeRange from '../Inputs/TimeRange';
import SelectInput from '../Inputs/SelectInput';
import AudioCheckRecord from '../Inputs/AudioCheckRecord';
import StaticReadOnly from '../Inputs/StaticReadOnly';


export default {
  name: 'InputSelector',
  props: {
    inputType: {
      type: String,
    },
    readOnly: {
      type: Boolean,
    },
    title: {
      type: String,
    },
    valueConstraints: {
      type: Object,
    },
    init: {

    },
    selected_language: {
      type: String,
    },
    showPassOptions: {
      type: Object,
    },
    preamble: {
      type: String,
    },
  },
  components: {
    Radio,
    AudioRecord,
    TextInput,
    IntegerInput,
    DateInput,
    DocumentUpload,
    MultiTextInput,
    SliderInput,
    MultiPart,
    TimeRange,
    SelectInput,
    AudioCheckRecord,
    StaticReadOnly,
  },
  data() {
    return {

    };
  },
  methods: {
    skip() {
      this.$emit('skip');
    },
    dontKnow() {
      this.$emit('dontKnow');
    },
    sendData(val) {
      if (val instanceof Date) {
        this.$emit('valueChanged', val.getFullYear());
      } else this.$emit('valueChanged', val);
      this.$emit('next');
    },
  },
};
</script>

<style>
  .scroll {
    position: relative;
    max-height: 400px;
    overflow-y: auto;
  }

  .scroll::-webkit-scrollbar {
    width: 0.5em;
  }

  .scroll::-webkit-scrollbar-track {
      -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  }

  .scroll::-webkit-scrollbar-thumb {
    background-color: darkgrey;
    outline: 1px solid slategrey;
    margin-left: 0.2em;
  }

</style>
