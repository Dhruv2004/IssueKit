# ![Imgur](http://i.imgur.com/UXN1tVV.png) IssueKit
A drop-in component for creating GitHub issues in your app.
**You should only have this in debug builds.**

![Screenshot](http://i.imgur.com/vyjd3sMl.png?1)

# How to use

Get an API access token from [GitHub ](https://github.com/settings/applications):

![Access token image](http://i.imgur.com/cJqyqam.png)

And **if you want image uploads**, [create an 'anonymous' imgur application](http://api.imgur.com/oauth2/addclient) and note its client ID.

![Client ID image](http://i.imgur.com/ZH3YA4B.png)

Go to the IssueKit directory in Terminal and run

```bash
sudo gem install cocoapods
pod install
```

Setup `ISKIssueManager` in `application:didFinishLaunchingWithOptions:`

```Objective-C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    // Reponame must be in 'username/reponame' format.

    [[ISKIssueManager defaultManager] setupWithReponame:@"usepropeller/IssueKit" andAccessToken:@"access token"];

    // If you have an imgur client ID
    [[ISKIssueManager defaultManager] setupImageUploadsWithClientID:@"your key here"];

    return YES;
}
```

Call `-presentIssueViewControllerOnViewController` when you want to show the issue prompt.

```Objective-C
- (IBAction)showIssueViewController:(id)sender {
    [[ISKIssueManager defaultManager] presentIssueViewControllerOnViewController:self];
}
```

That's it! IssueKit will create an issue with an 'IssueKit' label on the repo you specified.