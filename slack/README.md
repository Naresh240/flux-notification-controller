# Sending Notifications to Slack Channel

# Create New App under slack
````
https://api.slack.com/apps?new_app=1
````

![image](https://user-images.githubusercontent.com/58024415/163663191-80c39e0d-6e3b-4fa2-a795-72c50ef0f811.png)

````Click on Create New App````

![image](https://user-images.githubusercontent.com/58024415/163663187-8c262c85-245f-437b-a93c-bbb8cab3e70c.png)

````Click on From Scratch````

![image](https://user-images.githubusercontent.com/58024415/163663257-0a064f48-df08-4d87-b779-fc08701652c7.png)

````Provide name and workspace details````

![image](https://user-images.githubusercontent.com/58024415/163663273-a0fc6594-4b6f-4c92-a1fd-d4189fcb2444.png)

````Incoming webhook````

![image](https://user-images.githubusercontent.com/58024415/163663281-8d67a115-b1a4-4705-93b4-b7251a946ee7.png)

````Activate Incoming webhook````

![image](https://user-images.githubusercontent.com/58024415/163663297-3288da75-d754-44d3-a784-f643a570c3bc.png)

````Below we can see for creating a new Incoming webhook for workspace````

![image](https://user-images.githubusercontent.com/58024415/163663802-1b628813-5248-4146-ba9a-1cc4386aeb90.png)

````Click on Allow````

![image](https://user-images.githubusercontent.com/58024415/163663337-7116c595-b155-4889-b30e-3a4b93d2cb99.png)

````Copy Webhook URL````

# Open Below URL for slack app
````
https://app.slack.com/
````
# Define Provider
1. create a secret with your Slack incoming webhook:

````
kubectl -n flux-system create secret generic slack-url \
--from-literal=address=https://hooks.slack.com/services/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
````
2. Create a notification provider for Slack by referencing the above secret:
````
kubectl apply -f slack-provider.yaml
````
3. Create Alert
````
kubectl apply -f slack-alert.yaml
````
# Check notifications in slack channel
