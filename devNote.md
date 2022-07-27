# Development Note

## Multiple register file operand collector design

1. Map different ranges of register to different register files
2. Each register file will have number of banks and ports configured
3. The register number in inst will be convert to true register number within its register file
    1. if we have reg 0~15 mapped to RF0, and reg 16~31 mapped to RF1
    2. reg 16 will become reg 0 within RF1 when assigning banks