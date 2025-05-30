# Freeway Traffic Anomalous Event Detection Dataset
Early and accurate detection of anomalous events on the freeway, such as accidents, can improve emergency response and clearance. However, existing delays and errors in event identification and reporting make it a difficult problem to solve. Current large-scale freeway traffic datasets are not designed for anomaly detection and ignore these challenges. Therefore, we introduce the Freeway Traffic Anomalous Event Detection Dataset, the first large-scale lane-level freeway traffic dataset for anomaly detection. Our dataset consists of a month of weekday radar detection sensor data collected in 4 lanes along an 18-mile stretch of Interstate 24 heading toward Nashville, TN, comprising over 3.7 million sensor measurements. We also collect official crash reports from the Nashville Traffic Management Center and manually label all other potential anomalies in the dataset. This dataset has the potential to be used for developing and benchmarking anomaly detection methods to enchance automatic incident detection methods and reduce reporting delays.

## Dataset Description

The dataset consists of the following features.
- **time_unix**: the time the measurement was taken.
- **milemarker**: location of sensor on the interstate. This comes from the Tennessee Department of Transportation's coordination system and is consistent with what is labeled on the road.
- **lane**: the lane number. There are four lanes, where lane 1 is the left-most lane.
- **speed**: 30-second average speed of the vehicles passing through the area.
- **occupancy**: 30-second average percentage of time that the detection zone of the radar sensor is occupied by a vehicle.
- **volume**: 30-second average number of vehicles passing through the area.
- **crash_record**: whether a crash was officially reported at this timestamp.
- **human_label**: human anomaly label for this timestamp.

There are 196 nodes, across the 4 lanes and 49 milemarkers. Data was recorded using a Radar Detection System (RDS) sensor every 30 seconds weekday mornings (4:00 AM - 12:00 PM) in October, 2023. There are 3,763,200 data points.

## Using the Data

See the [Demo.ipynb](./Demo.ipynb) for a tutorial on how to load the data from the [nashville_freeway_anomaly.csv](./nashville_freeway_anomaly.csv) file. This notebook requires the following Python packages:

- numpy
- pandas
- matplotlib
- networkx (OPTIONAL)
- torch_geometric (OPTIONAL)

## Additional Resources

### Supplementary Data

To address issues with seasonality in the data, we have processed and released another 11 months of data! That data is hosted on a [Box Link](https://vanderbilt.box.com/s/f2hs7pvrivdzgzklui31uvutwggbuttz). So far, we have added 1 full week from each month. We are actively processing the rest of the data, then we will run our smoothing algorithm to handle missing data. We are also working on obtaining and processing the crash event logs for this time frame.

This Box folder includes the raw event logs corresponding to all data that can provide additional context about incidents.

It also includes a CSV with timestamps where we expect crashes to have actually occurred which may be useful for defining true positives. 

### Paper Link

- [arXiv](https://arxiv.org/abs/2406.15283)

### Interactive Website

Visit https://acoursey3.github.io/ft-aed/ to interact with the data without needing to download the dataset!

### Anomaly Detection Code

See https://github.com/acoursey3/freeway-anomaly-code/ for our anomaly detection code used for the paper's experiments.

## Citation

If you find this dataset useful for your research, please consider using the following citation!

```
@article{coursey2024ft,
  title={FT-AED: Benchmark dataset for early freeway traffic anomalous event detection},
  author={Coursey, Austin and Ji, Junyi and Quinones Grueiro, Marcos and Barbour, William and Zhang, Yuhang and Derr, Tyler and Biswas, Gautam and Work, Daniel},
  journal={Advances in Neural Information Processing Systems},
  volume={37},
  pages={15526--15549},
  year={2024}
}
```

## License
See the `LICENSE` file for the license. Note that the supplementary materials of the paper suggest this dataset is licensed under a CC BY-NC license. Upon further consideration, we have chosen a different license and the materials will be updated appropriately.
