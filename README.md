# Energy Profiling Plugin for TensorBoard

## Overview

In the first moment, this first version we pretend read a fake power data, and display on tensorboard. In the next versions we pretend to link IPMI with database and read the power datas obtained from ipmi. And our goals aims to integrate trace viewer with IPMI, debbuging all bottlenecks with Power information in all long the process.

Now, i'll show how to setup the plugin:

All files under [`static/*`][static-dir] are served as static assets, with the frontend entry point being [`static/index.js`][static-index-js]. The plugin backend serves scalar summaries (e.g. values written by [`tf.summary.scalar`][summary_scalar_docs]) from runs within the `--logdir` passed to TensorBoard.

[static-dir]: ./energy_profiling_plugin/static
[static-index-js]: ./energy_profiling_plugin/static/index.js

## Getting started

To generate some fake power data, you can run the [`demo.py`](energy_profiling_plugin/demo.py). 


Copy the directory `/energy_profiling_plugin` into a desired folder. In a virtualenv with TensorBoard installed, run:

```
python setup.py develop
```

This will link the plugin into your virtualenv. Then, just run

```
tensorboard --logdir /tmp//tmp/runs_energy_data
```

and open TensorBoard to see the raw scalars example tab.

After making changes to [`static/index.js`](./energy_profiling_plugin/static/index.js) or adding assets to `static/`, you can refresh the page in your browser to see your changes. Modifying the backend requires restarting the TensorBoard process.

To uninstall, you can run

```
python setup.py develop --uninstall
```

to unlink the plugin from your virtualenv, after which you can also delete the `energy_profiling_plugin.egg-info/` directory that the original `setup.py` invocation created.
