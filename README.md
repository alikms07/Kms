# ansible-prototype

Deploy the osmo-epdg and epc (IMS is deployed but untested yet).

See https://osmocom.org/projects/osmo-epdg/wiki/Hosted_epdg_playground for further information on the setup.

## To install

The setup expect to have a private network available with layer 2 connectivity between the 3 hosts.
Additional you need to setup the strongswan and osmo-epdg as both only prepare, but not installed.

```
ansible-playbook -i hosts epdg.yml epc.yml ims.yml
```

```
cd /srv/strongswan
./autogen.sh
./configure \
	--enable-eap-aka \
	--enable-eap-aka-3gpp \
	--enable-eap-aka-3gpp2 \
	--enable-eap-simaka-reauth \
	--enable-systemd \
	--enable-save-keys \
	--enable-p-cscf \
	--enable-osmo-epdg
make && make install
systemctl daemon-reload
systemctl restart strongswan
```

```
cd /srv/osmo-edpg
rebar3 shell --config ./config/local.config
```
