# exwmsw.el

This package provides functions for monitor-independent manipulation of workspaces in EXWM.

## Usage

First, set up your monitors:

```elisp
(setq exwmsw-screen-current-index-plist '("DP-5" 0 "DP-3" 0 "HDMI-0" 0))
(setq left-screen "DP-5")
(setq center-screen "DP-3")
(setq right-screen "HDMI-0")
```

Then, set up some keybindings:

```elisp
(exwm-input-set-key (kbd "s-a") #'exwmsw-cycle-screens)
(exwm-input-set-key (kbd "s-w") #'exwmsw-switch-to-left-screen)
(exwm-input-set-key (kbd "s-e") #'exwmsw-switch-to-center-screen)
(exwm-input-set-key (kbd "s-r") #'exwmsw-switch-to-right-screen)
(exwm-input-set-key (kbd "s-C-w") #'exwmsw-swap-displayed-workspace-with-left-screen)
(exwm-input-set-key (kbd "s-C-e") #'exwmsw-swap-displayed-workspace-with-center-screen)
(exwm-input-set-key (kbd "s-C-r") #'exwmsw-swap-displayed-workspace-with-right-screen)
(exwm-input-set-key (kbd "<f2>") #'exwmsw-cycle-workspace-on-left-screen)
(exwm-input-set-key (kbd "<f3>") #'exwmsw-cycle-workspace-on-center-screen)
(exwm-input-set-key (kbd "<f4>") #'exwmsw-cycle-workspace-on-right-screen)
(exwm-input-set-key (kbd "<f1>") #'exwmsw-create-workspace-on-current-screen)
(exwm-input-set-key (kbd "s-x") #'exwmsw-delete-workspace-on-current-screen)
```

Lastly, you can advise functions to create workspaces and delete workspaces automatically:
```elisp
(exwmsw-advise-screen-session #'mu4e #'mu4e-quit)
```

You can undo an advice as well:

```elisp
(exwmsw-unadvise-screen-session #'mu4e #'mu4e-quit)
```
