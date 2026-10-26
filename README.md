# DarwinBoot

UEFI XNU loader with packed RAM disk handoff support.

The kernel can be the prelinked Mach-O or its UEFI-compressed form, so a board
can keep the payload small enough for its BOOT partition. The payload step
writes the compressed file; DarwinBoot detects it by the missing Mach-O magic
and inflates it before parsing.

UniXNU passes the selected boot entry's arguments to DarwinBoot, which copies
them into XNU's command line and prints `DARWINBOOT: command line:` before
handoff. The top green bar marks `DarwinEnter` before cache maintenance,
MMU shutdown and the branch to XNU. Follow the
[boot argument workflow](https://unixnu.com/xnu/boot-arguments#apply-arguments)
and [green-bar diagnosis](https://unixnu.com/guide/debugging#green-bar).

Build and interface details: [documentation](https://unixnu.com/reference/components).
Sources and dependencies: [catalog](https://unixnu.com/reference/components).
