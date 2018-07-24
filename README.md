This repo reproduces the bug mentioned [here](https://github.com/facebook/flow/pull/4916#issuecomment-404096245) and filed [here](https://github.com/facebook/flow/issues/6631).

Flow's [declarations] section does not always work correctly. These are the steps to reproduce the issue: 
1. Create a new RN 0.55.4 project (`react-native init FlowDeclarations --version 0.55.4`)
2. Install Flow (`yarn add flow-bin@0.76.0`)
3. Run Flow

    At this point in the new RN project there are 15 Flow errors ( all inside `node_modules/react-native/Libraries/`).
4. Add the libraries with Flow errors to .flowconfig's [declarations] section
5. Run Flow again

**Actual result**: The above mentioned Flow errors remain and are not suppressed. More than that, there are new ones (now there are 47 errors)

**Expected result**: 15 Flow errors from the RN Libraries are suppressed, no new errors are added.


