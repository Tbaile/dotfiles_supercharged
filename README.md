Setup:
```bash
sudo dnf install -y $(cat fedora-requirements.txt)
pip install --user -r requirements.txt
ansible-galaxy install -r roles/requirements.yml
```

Launch Playbook (as user):
```bash
ansible-playbook --diff --ask-become-pass main.yml
```
