# 🛠️ AssetForge 🛠️ 
AssetForge is a simple asset manager application built in Daml.

### I. Overview 
This project was created by using `daml new capstone`. The project adopts and exemplifies the `proposal-accept` design pattern. 

The Proposer creates an AssetT instance representing a natural gas/water asset.
This asset can be proposed for transfer to another party (Acceptor), who can accept the transfer.
It is also possible to split the asset into two new (smaller) assets.

### II. Workflow
1. alice creates a AssetT contract     
2. alice exercises Asset_Transfer given price = 100.0 and nextOwner = bob
3. bob exercises AssetTransfer_Accept on the Asset_Transfer contract and gets the AssetT contract
4. bob exercises Asset_Split with splitAt = 0.6 on the AssetT contract, which yields two new AssetT contracts and archives the original

### III. Challenge(s)
* The project was created by using `daml new` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```
and the following was added:
```
exposed-modules:
  - Main
  - Test
```
For more info, check out [this post](https://discuss.daml.com/t/sandbox-options-wall-clock-time/5692/16?u=cathy_jung) on Daml Forum and [Daml Doc](https://docs.daml.com/tools/navigator/index.html?&_ga=2.48248804.337210607.1673989679-241632404.1672853064&_gac=1.17025355.1673455980.CjwKCAiA2fmdBhBpEiwA4CcHzfI2w1_D95zAr3_d6QTypOMXGTpUxtS06c55inucNwZvUZn4AebsJxoCZEgQAvD_BwE&_gl=1*elem6v*_ga*MjQxNjMyNDA0LjE2NzI4NTMwNjQ.*_ga_GVK9ZHZSMR*MTY3Mzk5NDQzOS4zMS4xLjE2NzM5OTQ3MDcuMC4wLjA.#logging-in-as-a-party).

### IV. Compiling & Testing
To compile and test:
```shell
$ daml test --files daml/Test.daml` 
```

OR run:

```shell
$ daml start
```

