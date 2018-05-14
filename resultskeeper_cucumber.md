
## Results Keeper 
Reults Keeper is a tool that allows to collect and monitor Cucumber (Ruby) test results in real time.

http://results-keeper.com/welcome

Below you can see some example of usage:

Watch all the builds 
![Image of Results Keeper](http://results-keeper.com/imgs/gallery/revisions.png)

See the particular test results (history)
![Image2 of Results Keeper](http://results-keeper.com/imgs/gallery/test.png)

Analyze errors
![Image3 of Results Keeper](http://results-keeper.com/imgs/gallery/error.png)
and more

# Get Started

  1. Install the gem

```
gem install results_keeper
```
        
  2. Add the following code to your env.rb or any file in "features/support" folder
```
if ENV['SEND_RK_RESULTS']
  require 'results_keeper'

  ResultsKeeper.instance.send_revision

  Before do |scenario|
    ResultsKeeper.instance.test_started(scenario)
  end

  After do |scenario|
    ResultsKeeper.instance.send_test(scenario)
  end

  at_exit do
    ResultsKeeper.instance.send_revision_complete
  end
```
end

  3. Create a Results Keeper account (http://results-keeper.com/company/sign_up)
  
  4. Click on Your Name link at the top 
  
  5. Copy your secret key 
  
  6. Run your tests using the following command:

```
SEND_RK_RESULTS=true RK_SECRET_KEY=XXXXXXX-XXXXXXXX-XXXX-XXXXXXXXX cucumber
```
You can export the copied key, and you won't need to write it each time when you run your tests (not mandatory)
```
export RK_SECRET_KEY=XXXXXXX-XXXXXXXXXXXX-XXXXXX
export SEND_RK_RESULTS=true
```
Now you can send your test results using only one simple command:
```
cucumber
```
Also you can add it to .bashrc, and not to export all the time manually

```
echo "export SEND_RK_RESULTS=true" >> ~/.bashrc
echo "export RK_SECRET_KEY=XXXXXXX-XXXXXXXXXXXX-XXXXXX" >> ~/.bashrc
```

Send screenshots of failed tests:
```
RK_SEND_SCREENSHOTS=true cucumber
```
Save results to your own project name:
```
RK_PROJECT_NAME=test cucumber
```
Save results to your own revision name:
```
RK_REVISION_NAME=revision_001 cucumber
```
Send results to the server:
```
SEND_RK_RESULTS=true
```
