---
layout: default
title: DigColPs_Integration_Manual
nav_order: 3
parent: DigColPs
---
{% raw %}
[1 Dependencies [2](#dependencies)](#dependencies)

[1.1 SWCs [2](#swcs)](#swcs)

[1.2 Global Functions(Non RTE) to be provided to Integration Project
[2](#global-functionsnon-rte-to-be-provided-to-integration-project)](#global-functionsnon-rte-to-be-provided-to-integration-project)

[2 Configuration [3](#configuration)](#configuration)

[2.1 Build Time Config [3](#build-time-config)](#build-time-config)

[2.2 Configuration Files to be provided by Integration Project
[3](#configuration-files-to-be-provided-by-integration-project)](#configuration-files-to-be-provided-by-integration-project)

[2.2.1 Da Vinci Parameter Configuration Changes
[3](#da-vinci-parameter-configuration-changes)](#da-vinci-parameter-configuration-changes)

[2.2.2 DaVinci Interrupt Configuration Changes
[3](#davinci-interrupt-configuration-changes)](#davinci-interrupt-configuration-changes)

[2.2.3 Manual Configuration Changes
[3](#manual-configuration-changes)](#manual-configuration-changes)

[3 Integration [4](#integration)](#integration)

[3.1 Required Global Data Inputs
[4](#required-global-data-inputs)](#required-global-data-inputs)

[3.2 Required Global Data Outputs
[4](#required-global-data-outputs)](#required-global-data-outputs)

[3.3 Specific Include Path present
[4](#specific-include-path-present)](#specific-include-path-present)

[4 Runnable Scheduling [5](#runnable-scheduling)](#runnable-scheduling)

[5 Memory Mapping [6](#memory-mapping)](#memory-mapping)

[5.1 Mapping [6](#mapping)](#mapping)

[5.2 Usage [6](#usage)](#usage)

[5.3 Non RTE NvM Blocks [6](#non-rte-nvm-blocks)](#non-rte-nvm-blocks)

[5.4 RTE NvM Blocks [6](#rte-nvm-blocks)](#rte-nvm-blocks)

[6 Compiler Settings [6](#compiler-settings)](#compiler-settings)

[6.1 Preprocessor MACRO [6](#preprocessor-macro)](#preprocessor-macro)

[6.2 Optimization Settings
[6](#optimization-settings)](#optimization-settings)

[7 Revision Control Log
[7](#revision-control-log)](#revision-control-log)

# Dependencies

## SWCs

| Module  | Required Feature |
|---------|------------------|
| I2cNxtr | All functions    |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
refered. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration

## Build Time Config

| Modules | Notes |     |
|---------|-------|-----|
| None    |       |     |

##  [section]

## Configuration Files to be provided by Integration Project

### Da Vinci Parameter Configuration Changes

| Parameter | Notes | SWC |
|-----------|-------|-----|
| None      |       |     |

### DaVinci Interrupt Configuration Changes

| ISR Name | VIM \# | Priority Dependency | Notes |
|----------|--------|---------------------|-------|
| None     |        |                     |       |

### Manual Configuration Changes

The following settings need to be configured in I2cNxtr_Cfg.h – a
template of which can be found in the include directory of the I2cNxtr
component.

| Constant                 | Notes                                                                         | SWC     |
|-----------------------------|----------------------------------|----------|
| D_COMMBUFFERSIZE_CNT_U08 | 3                                                                             | I2cNxtr |
| I2c_Notification         | DigColPsInt_InterruptNotification                                             | I2cNxtr |
| D_I2CREG_STRCPTR         | i2cREG1                                                                       | I2cNxtr |
| D_VCLK_HZ_F32            | Set to corresponding VCLK frequency, commonly 8000000.0 for a 160.0 MHz part. | I2cNxtr |

# Integration

## Required Global Data Inputs

None

## Required Global Data Outputs

None

## Specific Include Path present

Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

| Init           | Scheduling Requirements | Trigger   |
|----------------|-------------------------|-----------|
| DigColPs_Init1 | None                    | RTE(Init) |

| Runnable      | Scheduling Requirements               | Trigger    |
|---------------|---------------------------------------|------------|
| DigColPs_Per1 | Early in 2 ms task to minimize jitter | RTE (2 ms) |
| DigColPs_Per2 | None                                  | RTE (4 ms) |

**.**

# Memory Mapping

## Mapping

| Memory Section                             | Contents     | Notes |
|--------------------------------------------|--------------|-------|
| DIGCOLPS_START_SEC_VAR_CLEARED_32          | float32      |       |
| DIGCOLPS_START_SEC_VAR_CLEARED_16          | uint16       |       |
| DIGCOLPS_START_SEC_VAR_CLEARED_8           | uint8, sint8 |       |
| DIGCOLPS_START_SEC_VAR_CLEARED_BOOLEAN     | Boolean      |       |
| DIGCOLPS_START_SEC_VAR_CLEARED_UNSPECIFIED | LPF32KSV_Str |       |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

| Feature | RAM | ROM |
|---------|-----|-----|
| None    |     |     |

Table 1: ARM Cortex R4 Memory Usage

## Non RTE NvM Blocks

| Block Name |
|------------|
| None       |

Note : Size of the NVM block if configured in developer

##  RTE NvM Blocks

| Block Name          |
|---------------------|
| Rte_Pim_DigColPsEOL |

Note : Size of the NVM block if configured in developer

# Compiler Settings

##  Preprocessor MACRO

None

## Optimization Settings

None

##  [section-1]

# Revision Control Log

| **Rev \#** | **Change Description**     | **Date**  | **Author** |
|------------|----------------------------|-----------|------------|
| 1          | Initial component creation | 22-Aug-13 | Jared      |

{% endraw %}