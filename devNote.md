# Development Note

## Multiple register file operand collector design

1. Map different ranges of register to different register files
2. Each register file will have number of banks and ports configured
3. The register number in inst will be convert to true register number within its register file
    1. if we have reg 0~15 mapped to RF0, and reg 16~31 mapped to RF1
    2. reg 16 will become reg 0 within RF1 when assigning banks

### Configure file options

1. `-gpgpu_operand_collector_num_regfiles UINT32`: specify the number of registerfiles inside operand collector
2. `gpgpu_operand_collector_regfile_num_ports UINT32:UINT32:...`: colon separated vector to specify number of ports for each regfile
3. `gpgpu_operand_collector_regfile_num_banks UINT32:UINT32:...`: colon separated vector to specify number of banks for each regfile
4. `gpgpu_operand_collector_regfile_num_registers UINT32:UINT32:...`: colon separated vector to specify number of architectural registers for each regfile
    1. `256:256` specified 256 registers each for the two registerfiles
    2. meaning `R0~255` will be mapped to ports and banks of the first registerfile and register `R256~511` will be mapped to the second registerfile

## Run env setup script from zsh

`BASH_SOURCE=~/SST-Integration/env-setup/11.0_env_setup.sh emulate zsh -c '. "$BASH_SOURCE"'`