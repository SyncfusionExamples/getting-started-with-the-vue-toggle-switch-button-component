<script setup>
  import { SwitchComponent } from '@syncfusion/ej2-vue-buttons';
  import {ref} from 'vue';
  const isBluetoothOn = ref(false);
  const devices = [
    { id: 1, name: 'Mark iPhone'},
    { id: 2, name: 'POCO 3901' },
    { id: 3, name: 'ANDROID 18' }
  ];

  const onChange = (args) =>{
    isBluetoothOn.value = args.checked;
  }
</script>

<template>
  <div className="container">
    <label className="label"> Bluetooth Tethering</label>
    <SwitchComponent
      onLabel="On"
      offLabel="Off"
      cssClass="e-small"
      @change="onChange"
      :disabled="true"
    ></SwitchComponent>
  </div>
  <div className="bluetooth-list" v-if="isBluetoothOn">
    <span className="bluetooth-header"> Available Devices</span>
    <ul className="device-list">
      <li className="device-item" v-for="device in devices" :key="device.id">
        <span classname="e-icon e-link"></span>
        <span>{{ device.name }}</span>
      </li>
    </ul>
  </div>
</template>

<style>
  @import "../node_modules/@syncfusion/ej2-base/styles/fluent.css";
  @import "../node_modules/@syncfusion/ej2-buttons/styles/fluent.css";
  @import "../node_modules/@syncfusion/ej2-icons/styles/material.css";

  .container{
    display: flex;
    flex-direction:row;
    align-items: center;
  }
  .label{
    margin-right:20px;
    font-size:larger;
  }
  .e-switch-wrapper{
    width:45px;
  }
  .bluetooth-header{
  font-size: larger;
  border-top: 1px solid;
  padding-top: 20px;
  width: 200px;
  display: block;
  }
  .bluetooth-list {
    width: 200px;
    margin-top: 50px;
  }
  .device-list{
  padding: 0px 0px 0px 10px;
  }
  .device-item {
    display: flex;
      align-items: center;
      padding: 10px;
  }
  .device-item .e-icons {
  margin-right: 0.5rem;
  color: #007bff; /* Icon color */
  }
  .device-item:hover {
    background-color: #f0f0f0;
    cursor: pointer;
  }

</style>