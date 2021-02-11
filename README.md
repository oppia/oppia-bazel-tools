This repository contains temporary artifacts pertaining to building Oppia
Android on Bazel.

In particular, it contains a version of android-tools.zip that, when used as an
override repository, will enable Bazel's 4.0 LTS version for use to build Oppia
Android.

In order to use this repository to be able to build Oppia Android, we suggest
using the following steps:
1. ``cd ~/opensource`` (or the directory containing your oppia-android repository).
2. ``git clone https://github.com/oppia/oppia-bazel-tools``
3. Update your ~/.bazelrc file to override the Android tools repository to point
   to this new location, and enable AndroidX testing. Or, just run this command
   (note that this overrides your profile-level bazelrc file, so you may want to
   copy this manually if you have other configurations already setup for Bazel):
   ```bash
   ASSETS_PATH=~/opensource/oppia-bazel-tools echo build --override_repository=android_tools="$(cd "$(dirname "$ASSETS_PATH")"; pwd)/$(basename "$ASSETS_PATH")" > ~/.bazelrc
   echo build --android_databinding_use_androidx > ~/.bazelrc
   ```

Note that the configuration setup to make this repository work is temporary &
will no longer be necessary once Bazel ships a version that includes the updated
Android tools repository.

Finally, note that all of the Bazel-related files in this repository pertain to
the Bazel project. Please see https://github.com/bazelbuild/bazel for licensing
& other details on the project from which these files originate.

