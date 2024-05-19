# DeployaMachineLearningModeltoaReal-TimeInferenceEndpoint

Based on https://aws.amazon.com/tutorials/machine-learning-tutorial-deploy-model-to-real-time-inference-endpoint/

Includes Autoscaling and Loadbalanceing test:

request_duration = 250
end_time = time.time() + request_duration
print(f"Endpoint will be tested for {request_duration} seconds")
while time.time() < end_time:
    csv_file = io.StringIO()
    test_sample = test_df.drop(["fraud"], axis=1).iloc[[np.random.randint(0, test_df.shape[0])]]
    test_sample.to_csv(csv_file, sep=",", header=False, index=False)
    payload = csv_file.getvalue()
    response = sm_runtime_client.invoke_endpoint(
                                                 EndpointName=endpoint_name,
                                                 Body=payload,
                                                 ContentType="text/csv"
                                                )
                                                
![image](https://github.com/Noel-Niko/DeployaMachineLearningModeltoaReal-TimeInferenceEndpoint/assets/83922762/43882efd-7a72-417b-819a-64bbec7a4481)
