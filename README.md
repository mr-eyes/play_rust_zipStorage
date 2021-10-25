# play_rust_zipStorage

## Create test text files

```sh
mkdir data && cd data

base64 /dev/urandom | head -c 10000000000 > 10GB.txt
base64 /dev/urandom | head -c 1000000000 > 1GB.txt
base64 /dev/urandom | head -c 100000000 > 100MB.txt

zip 10GB.zip 10GB.txt
zip 1GB.zip 1GB.txt
zip 10MB.zip 100MB.txt

mkdir tmp && cd tmp

mkdir -p dir1/dir2 dir3

base64 /dev/urandom | head -c 1000000 > root_001.txt
base64 /dev/urandom | head -c 1000000 > root_002.txt
base64 /dev/urandom | head -c 1000000 > root_dir1_001.txt
base64 /dev/urandom | head -c 1000000 > root_dir1_dir2_001.txt
base64 /dev/urandom | head -c 1000000 > root_dir1_dir2_002.txt
base64 /dev/urandom | head -c 1000000 > root_dir3_001.txt
base64 /dev/urandom | head -c 1000000 > root_dir3_002.txt

mv root_dir1_dir2* dir1/dir2/
mv root_dir1* dir1
mv root_dir3* dir3

zip -r nested_data.zip .
mv nested_data.zip ../

cd ..

```