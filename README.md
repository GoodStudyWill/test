# test

------------------Ixiao---------
#==================工程配置参数===================
#客户端版本号，此参数将替换工程原来的版本号，命名规范：{测试包：x.y.z(3段)，生产验证包：x.y.z.yymmdd(4段)}
ls
echo "EM_VERSION"
EM_VERSION=${EM_VERSION}

#工程名称
PROJ_NAME=FJSEMarketing

#Bundle ID
BUNDLE_ID=com.pingan.FJSEMarket

#环境，取值范围（int, stg1, stg2, prd, SS_stg2_pafu_stg1, SS_stg1_pafu_stg2, SS_stg3_pafu_stg1, SS_stg3_pafu_stg2）
CLIENT_EM=prd

#程序显示名称选项，取值范围（DEFAULT,TYPE_TIMESTAP）
APP_DISPLAYNAME_TYPE=DEFAULT

Version_Date="2017-12-12"
APP_FORCE_UPDATE=1
Open_OCLint=false

#===================编译配置参数==================
#编译目标
TARGET=FJSEMarketing

#编译使用的BaseSDK
SDK=iphoneos10.0

#最低支持的iOS系统版本
IPHONEOS_DEPLOYMENT_TARGET=8.0

#Debug或者Release
#CONFIGURATION=$CONFIGURATION
CONFIGURATION=Release

SCHEME=FJSEMarketing

SYMROOT=`pwd`

WC=FJSEMarketing.xcworkspace

#========================解压脚本======================
#unzip -o -d `pwd`\/CI ci.zip
ls

#========================调用构建脚本（iOS 4.2.0版本以上需要调用4.2.0版本的脚本iOS_build_420.sh）==========================
source `pwd`/CI/iOS_EMarket_release_100.sh $EM_VERSION $PROJ_NAME $CLIENT_EM $APP_DISPLAYNAME_TYPE $TARGET $SDK $IPHONEOS_DEPLOYMENT_TARGET $CONFIGURATION $SCHEME $SYMROOT $WC $Version_Date $APP_FORCE_UPDATE $Open_OCLint



--------------IS_USED_LOCAL_WEBPAGE_RESOURCE------------

#==================工程配置参数===================
#客户端版本号，此参数将替换工程原来的版本号，命名规范：{测试包：x.y.z(3段)，生产验证包：x.y.z.yymmdd(4段)}
RO_VERSION=${RO_VERSION}
#工程名称
PROJ_NAME=PARO
ls
#环境，取值范围（int, stg1, stg2, prd, SS_stg2_pafu_stg1, SS_stg1_pafu_stg2, SS_stg3_pafu_stg1, SS_stg3_pafu_stg2）
CLIENT_RO=${CLIENT_RO}

#程序显示名称选项，取值范围（DEFAULT,TYPE_TIMESTAP）
APP_DISPLAYNAME_TYPE=${APP_DISPLAYNAME_TYPE}


#是否使用本地资源包开关，取值范围{0:不使用；1:使用}【3.5.1版本新增配置项】
IS_USED_LOCAL_WEBPAGE_RESOURCE=${IS_USED_LOCAL_WEBPAGE_RESOURCE}

#===================编译配置参数==================
#编译目标
TARGET=PARO

#编译使用的BaseSDK
SDK=iphoneos10.0

#最低支持的iOS系统版本
IPHONEOS_DEPLOYMENT_TARGET=8.0

#Debug或者Release
CONFIGURATION=${CONFIGURATION}
SCHEME=PARO
SYMROOT=`pwd`
WC=PARO.xcworkspace
#unzip -o -d `pwd`\/CI CI.zip
#iOS资源包放置路径配置
paro_from=`pwd`\/ro.zip
paro_to=`pwd`\/PARO\/Resource\/ro.zip

#拼装H5资源压缩包拷贝到客户端的from-to列表
H5_ZIP_FROM_TO_LIST=${paro_from}:${paro_to}
Version_Date=${Version_Date}
APP_FORCE_UPDATE=${APP_FORCE_UPDATE}
HTML_FORCE_UPDATE=${HTML_FORCE_UPDATE}

#拼装H5资源模块初始版本号列表
H5_VERSION_LIST=@\"ro\":@\"${H5_VERSION_FOR_PARO}\"
#========================调用构建脚本（iOS 4.2.0版本以上需要调用4.2.0版本的脚本iOS_build_420.sh）==========================
source `pwd`/CI/iOS_RO_release_100.sh $RO_VERSION $PROJ_NAME $CLIENT_RO $APP_DISPLAYNAME_TYPE $TARGET $SDK $IPHONEOS_DEPLOYMENT_TARGET $CONFIGURATION $IS_USED_LOCAL_WEBPAGE_RESOURCE $SCHEME $SYMROOT $WC $H5_ZIP_FROM_TO_LIST $H5_VERSION_LIST $Version_Date $APP_FORCE_UPDATE $HTML_FORCE_UPDATE
