# install_esp_idf
GitHub action to install esp-idf and cache its dependencies

## Prerequisite
Your firmware repo must have the esp-idf as submodule at the repository root. If it is somewhere else, specify with `idfpath`.

## Example workflow

```yaml
name: Build firmware

on: push

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Fast Submodule Checkout esp-idf
      uses: 0xFEEDC0DE64/fast_submodule_checkout@main
      with:
        submodule: esp-idf

    - name: Install esp-idf
      uses: 0xFEEDC0DE64/install_esp_idf@main
      #with:
      #  idfpath: esp-idf

    - name: Build firmware
      run: |
        . esp-idf/export.sh
        idf.py build
```


