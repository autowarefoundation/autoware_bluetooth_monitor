# autoware_bluetooth_monitor

This ROS 2 package monitors Bluetooth connections and publishes connection diagnostics. It uses a separate `l2ping_service` process for Bluetooth queries. See the [package documentation](autoware_bluetooth_monitor/README.md) for parameters and runtime setup.

The package comes from [Autoware Universe at `274d576f11a9b805f124c018fc3a5e3790560353`](https://github.com/autowarefoundation/autoware_universe/tree/274d576f11a9b805f124c018fc3a5e3790560353/system/autoware_bluetooth_monitor). The source license, notices, maintainers, and changelog remain with the package.

## Installation

If your workspace already contains this package in Autoware Universe, use a Universe revision that removes it before you import this repository. Stable Autoware releases that still contain the package cannot use both copies in one workspace.

After the package appears in the Autoware Index, run these commands from your Autoware workspace root:

```sh
aw-index-cli compose --rosdistro jazzy --packages autoware_bluetooth_monitor
vcs import src < repositories/autoware-index.repos
rosdep install --from-paths src --ignore-src --rosdistro jazzy -y
colcon build --symlink-install --packages-up-to autoware_bluetooth_monitor
source install/setup.bash
```

## CI

The `autoware-index-validate` workflow builds the package, runs its ament lint tests, and runs clang-tidy against the latest published Autoware Core image for Jazzy. It runs on pull requests, pushes to `main`, and manual requests. Core dependencies come from the image. Hardware tests and a running Bluetooth service are separate from these checks.

The daily `sync-files` workflow maintains the shared files listed in [`.github/sync-files.yaml`](.github/sync-files.yaml) from the Foundation templates. The package-specific Index validation workflow remains local to this repository.

Sync Files requires the Foundation GitHub App to have repository access, the `APP_ID` and `PRIVATE_KEY` secrets, and repository auto-merge enabled. Public pull requests use pre-commit.ci for formatting checks. Run `pre-commit run --all-files` before you open a pull request.
