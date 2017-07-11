# [ Space Commander]
[中文说明点这里](http://www.jianshu.com/p/fd2e453ef07f)

**[ Space Commander]** provides tools which enable a team of iOS developers to commit Objective-C code to a git repository using a unified style format, without requiring any manual fixup.

This branch is forked from square/spacecommander. I modified **[setup-repo.sh]** and  **[format-objc-hook]**, to make these functions come true :
1. automatic format and submit without copying commands to format codes manually.
2. change the way to enable or disable format files

Installation Locally
-------------
1. clone or download this repository to your mac. The spaceCommanderPath, for example: /Users/young/Documents/iOS/spacecommander-whoyoung.
2. cd "your target project's path" in terminal. For example: `cd /Users/young/Documents/iOS/testClangFormat`. Then run the command (notice: the path should be replaced by your spacecommander's path): `"/Users/young/Documents/iOS/spacecommander-whoyoung"/setup-repo.sh `

Usage
-------------

After running `setup-repo.sh`, modifying your project files, clicking sourcetree's button - "submit", then, formatting checks and commit will run automatically.

Acquiescently, format and submit automatically. If you want disable format automatically, just open **[pre-commit]**: `vim /Users/young/Documents/iOS/testClangFormat/.git/hooks/pre-commit` (notice: the path should be replaced by your project's path), modify script like this:
```
#!/usr/bin/env bash
current_repo_path=$(git rev-parse --show-toplevel)
repo_to_format="/Users/young/Documents/iOS/testClangFormat"

#enable auto-format
#if [ "$current_repo_path" == "$repo_to_format" ] && [ -e "/Users/young/Documents/ios/spacecommander-whoyoung"/format-objc-hook ]; then "/Users/young/Documents/ios/spacecommander-whoyoung"/format-objc-hook || exit 1; fi

#disable auto-format
if [ "$current_repo_path" == "$repo_to_format" ] && [ -e "/Users/young/Documents/ios/spacecommander-whoyoung"/format-objc-hook ]; then "/Users/young/Documents/ios/spacecommander-whoyoung"/format-objc-hook -false || exit 1; fi
```

More Details
-------------

For more details, please references main repository [spacecommander](https://github.com/square/spacecommander)  


