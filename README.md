# NVIDIA-Deepstream-Occupancy-Analytics
Running NVIDIA Deepstream application for Occupancy Analysis

This repo is mainly focused on the NVIDIA Deepstream SDK. It takes streaming video as input, counts the number of people crossing a tripwire(used NvDsAnalytics plugin to draw line and count people crossing the line) and sends the live data to the cloud. Here I am using PeopleNet model from NVIDIA TAO and Intergrating the same with the Deepstream-app. 

I have have ran this repo successfully on NVIDIA Jetson TX2 Dev kit 8GB Bearing Jetpack 4.6.3. 

## Step 1: Clone the repository

**Note : Make sure that you are in */opt/nvidia/deepstream/deepstream-6.0/sources/apps/sample_apps/* directory**

clone https://github.com/NVIDIA-AI-IOT/deepstream-occupancy-analytics

## Step 2: Download and Install Kafka Messenger
- Install Kafka: [https://kafka.apache.org/quickstart] and create the kafka topic:
  
> **$ tar -xzf kafka_2.13-3.5.0.tgz**

> **$ cd kafka_2.13-3.5.0**

**Below commands have to compiled in different terminals(one command in one terminal)**

> **$ bin/zookeeper-server-start.sh config/zookeeper.properties**

> **$ bin/kafka-server-start.sh config/server.properties**

> **$ bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092**

## Step 3 : Download the model
- **Download peoplnet model: cd deepstream-occupancy-analytics/config && ./model.sh**

## Step 4: Build and Configure
**Set CUDA_VER in the MakeFile as per platform.**

> **For Jetson, CUDA_VER=11.4**

> **cd deepstream-occupancy-analytics && make**

**Set msg-conv-msg2p-lib at [sink1] group in dstest_occupancy_analytics.txt as per platform**

For Jetson : msg-conv-msg2p-lib=$DEEPSTREAM_SDK_PATH/deepstream-occupancy-analytics/bin/jetson/libnvds_msgconv.so

**Note : change $DEEPSTREAM_SDK_PATH with /opt/nvidia/deepstream/deepstream-6.0/sources/apps/sample_apps/**


Follow the steps to run your Deepstream Occupancy Analytics Successfully.

1. **Run the below command to intialise the Deepstream application**
   
   >**./deepstream-test5-analytics -c config/dstest_occupancy_analytics.txt**

2. **In another terminal run this command to see the kafka messages:**

   >**bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092**

Note : Use the **sudo** since you are running

After entering the above model, you shouldd be running the application successfully.
