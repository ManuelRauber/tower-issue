# Tower Issue

Hi Tower!

Thanks for taking time to look into this possible issue!

As explained in the support ticket (#109656), Tower can not do commits in this repo.
Please get all information from the ticket.
And then follow this README on how to do the setup.

If you have any other questions, please use the ticket.

## Setup

In order to make everything work, you need [Flutter](https://docs.flutter.dev/get-started/install/macos) installed. 

If you're using Homebrew, simply run `brew install flutter`.
It does not matter if you install Flutter via Homebrew or via the link above, in both cases the issue will show up.
You should not need any Android or iOS SDKs, because we're not building the app, but run git commands only (which will invoke some flutter build stuff, but to my knowledge does not require any other SDK.).

After installing, open a terminal in the folder, where this readme is located and run:

```bash
dart run husky install
```

This will enable the git hooks.

## Trigger the issue

To trigger the issue, we need a simple change in the code. 
Open `lib/main.dart`, there is a simple line with a comment: `// x`.
Just remove the comment and using Tower try to make a commit (adhering to conventional commit standard, so as a commit message try `feat: some changes`). 
It will take some time and then there should be the message:

```text
The current Flutter SDK version is 0.0.0-unknown.

Because app_settings 5.0.0 requires Flutter SDK version >=3.7.0 and no versions of app_settings match >5.0.0 <6.0.0, app_settings ^5.0.0 is forbidden.
So, because tower_issue depends on app_settings ^5.0.0, version solving failed.
```

If you try to make the same commit via command line:

```bash
git commit -am "feat: this will work"
```

It will take some time as well, but it will succeed.