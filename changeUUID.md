
refer to
https://github.com/CCChieh/IBMYes/issues/13

breif configuration:

## ORIGINAL CONFIGURATION
```
install(){
    echo "进行安装。。。"
    cd ${SH_PATH}/IBMYes/v2ray-cloudfoundry
    ibmcloud target --cf
    ibmcloud cf install
    ibmcloud cf push
    echo "安装完成。"
}
```

## ADD THREE NEW LINE
```
install(){
    echo "进行安装。。。"
    cd ${SH_PATH}/IBMYes/v2ray-cloudfoundry
    UUID=$(cat /proc/sys/kernel/random/uuid)
    echo "uuid: " $UUID
    sed -i "s/id\": .*\"/id\": \"$UUID\"/g" ./v2ray/config.json
    ibmcloud target --cf
    ibmcloud cf install
    ibmcloud cf push
    echo "安装完成。"
}
```

Then run install.sh in home directory,it will print uuid in the screen
