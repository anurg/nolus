# Nolus Snapshots

The Steps to resore from snapshot is as follows:

### Restoration from snapshot

Stop the service and reset the data

```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```

### Download latest snapshot

```
curl -L https://snapshots.nkbblocks.com/share/nolus-rila.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.nolus
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```

### Restart the service and check the log

```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```


