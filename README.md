# TD
A native terminal dictionary, with a few lines in bash and a collection of txt dictionaries.

## Usage
1. Download the txt dictionaries to *dictPath*
2. Put following lines to your zshrc or bashrc
```bash
unalise d
d() {
  blue=`echo -e "\e[1m\e[34m"` # specify format for dictionary name and word being looked in urxvt.
  norm=`echo -e "\e[0m"` # normal format in urxvt.
  dictPath=~/Dropbox/dictionaries/ # change this to your dictionaries' path
  pcregrep -M  "^$1\n.*" ${dictPath}*.txt \
    | sed "s/\/home.*dictionaries\/\(.*\)\.txt\(.*\)/${blue}\1\2${norm}/" \
    | perl -pe 's/(interj|n|v|adj|adv|conj|pron|prep)(?=\.)/\n\1/g'
}
```
## Demo
![vicon](https://github.com/d8660091/td/raw/master/vicon.png "Vicon")

![Chinese](https://github.com/d8660091/td/raw/master/chinese.png "Chinese")
