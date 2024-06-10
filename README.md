# NVIDIA-Deepstream-Occupancy-Analytics
Running NVIDIA Deepstream application for Occupancy Analysis

This repo is mainly focused on the NVIDIA Deepstream SDK. It takes streaming video as input, counts the number of people crossing a tripwire(used NvDsAnalytics plugin to draw line and count people crossing the line) and sends the live data to the cloud. Here I am using PeopleNet model from NVIDIA TAO and Intergrating the same with the Deepstream-app. 
