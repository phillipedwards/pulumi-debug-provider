# Debug (step-through) a Pulumi Provider 

## This repo contains an example showing how to debug a Pulumi provider using a IDE and a locally running provider.

## Requirements
1. IDE (this example uses VS Code)
2. Local copy of the Pulumi provider you want to debug
3. Pulumi program which uses the provider you want to debug (this example uses Pulumi Kubernetes)

## Steps
1. Create a launch configuration (VS Code) to execute the provider binary locally on your machine
2. Set a breakpoint somewhere within the provider code that will be triggered. In this case, we will set a breakpoint in ./provider/pkg/provider/provider.go
3. Start the provider binary through your IDE
4. Once the provider binary fullys starts, it will emit it's process ID in your debug output (terminal)
. Using the PID from step 3 execute a pulumi up. `PULUMI_DEBUG_PROVIDERS="{provider_name}:{process_id}" pulumi up|pre|etc` replacing {provider_name} with your provider (kubernetes in this case) and {process_id} with the PID from step 3.
5. Your breakpoint should have been reached and you can now step through the code as you wish!