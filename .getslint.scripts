#!/bin/sh
# vim: set syn=sh ft=sh et sw=2 sts=2 ts=2 tw=0:
#
# Used to download the correct version of Slint Scripts.

cd $(dirname "$0")
SLINT_SCRIPTS_VER="$1"
if [ -z "$SLINT_SCRIPTS_VER" ]; then
  echo "You need to specify a branch or tag for slint-scripts" >&2
  exit 1
fi
SLINT_SCRIPTS_URL='git://github.com/djemos/slint-scripts.git'

if [ -d slint-scripts ]; then
  rm -rf slint-scripts || echo "slint-scripts directory cannot be removed, check permissions" >&2
fi
git clone "$SLINT_SCRIPTS_URL" slint-scripts
# install symlinks
for a in 32 64 arm; do
  if [ -d $a ]; then
    for f in slint-scripts/*; do
      ln -s ../$f $a/
    done
  fi
done
