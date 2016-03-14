### Choosing Custom Ports

As of release `0.4.10`, you can specify an index for the dynamically allocated port Singularity should use when healthchecking and when adding the service to the load balancer. Previously, Singularity would always use the first dyanamically allocated port.

To change the healthcheck port, simply add:

```yaml
healthCheckPortIndex: 1 # or another integer
```

to your `SingularityDeploy` object. This will tell Singularity to use the dynamically allocated port at index 1 (i.e. second allocated port) when performing a health check.

Similarly, you can also specify the port index to use for the load balancer by specifying:

```yaml
loadBalancerPortIndex: 1 # or another integer
```

in your `SingularityDeploy` object. Keep in mind the dynamically alocated ports will be available to your process as environment variables in the format `PORT{index}` (e.g. `PORT0=32091` for a first dynamically allocaed port of 32091)