Instructions says:

cd duo-buildroot-sdk/
./build_milkv.sh


In ./build_milkv.sh:
build_all function is called

Then:

./build/milkvsetup.sh:function build_all()
./build/cvisetup.sh:function build_all()

Both call pack_boot
./build/common_functions.sh:function pack_boot                                           

pack_boot function copy boot.itb to boot.sd...:

./build/common_functions.sh:    command cp ./boot.itb "$OUTPUT_DIR"/rawimages/boot."$STORAGE_TYPE"

boot.itb file is generated with Makefile and target boot

Looks like I'd have to edit multi.its file to add my own kernel there to the image
./ramdisk/build/cv1800b_milkv_duo_sd/workspace/multi.its


https://www.rocketboards.org/foswiki/Documentation/SingleImageBoot
https://github.com/lentinj/u-boot/tree/master/doc/uImage.FIT
https://u-boot.readthedocs.io/en/latest/usage/cmd/bootm.html




Looks like all that is required is a the following partitioning scheme:
https://github.com/milkv-duo/duo-buildroot-sdk/blob/develop/milkv/gen_burn_image_sd.sh#L37
https://github.com/milkv-duo/duo-buildroot-sdk/blob/develop/milkv/genimage-milkv-duo.cfg

And to generate a boot.sd file
