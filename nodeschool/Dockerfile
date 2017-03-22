FROM node:slim
MAINTAINER Paul Amazona <whatevergeek@gmail.com>

# Install node and npm latest versions.
RUN apt-get update -qq && apt-get install -qqy software-properties-common curl && \
  curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
  apt-get install -qqy nodejs libfontconfig && \
  # Remove the install source for NPM as it's not very reliable.
  rm /etc/apt/sources.list.d/nodesource.list && \
  npm install -g npm && \
  # Adds fs-extra to npm and replaces the fs.rename method with the fs.extra
  # move method that now automatic chooses what to do (rename/move).
  # See https://github.com/npm/npm/issues/9863.
  cd $(npm root -g)/npm \
  && npm install fs-extra \
  && sed -i -e s/graceful-fs/fs-extra/ -e s/fs.rename/fs.move/ ./lib/utils/rename.js

# Install nodeschool libraries
RUN npm install -g learnyounode && \
npm install -g javascripting && \
npm install -g scope-chains-closures && \
npm install -g elementary-electron && \
npm install -g how-to-npm && \
npm install -g stream-adventure && \
npm install -g how-to-markdown && \
npm install -g functional-javascript-workshop && \
npm install -g expressworks && \
npm install -g makemehapi && \
npm install -g promise-it-wont-hurt && \
npm install -g async-you && \
npm install -g planetproto && \
npm install -g learnyoureact && \
npm install -g web-audio-school && \
npm install -g test-anything

# npm install -g esnext-generation && \
# npm install -g tower-of-babel && \
# npm install -g learnyoumongo && \
# npm install -g regex-adventure && \
# npm install -g learn-sass && \
# npm install -g learnyoubash && \
# npm install -g currying-workshopper && \
# npm install -g bacon-love && \
# npm install -g innersourceadventure && \
# npm install -g shader-school && \
# npm install -g bytewiser && \
# npm install -g bug-clinic && \
# npm install -g browserify-adventure && \
# npm install -g introtowebgl && \
# npm install -g count-to-6 && \
# npm install -g kick-off-koa && \
# npm install -g lololodash && \
# npm install -g learnyoucouchdb && \
# npm install -g learn-generators && \
# npm install -g perfschool && \
# npm install -g torrential && \
# npm install -g node-debug-school && \
# npm install -g seneca-in-practice && \
# npm install -g less-is-more && \
# npm install -g js-best-practices

# npm install -g levelmeup
# npm install -g nodebot-workshop
# npm install -g goingnative
# npm install -g webgl-workshop
# npm install -g thinking-in-react

### Install additional utilities
RUN apt-get update && apt-get install -y \
    ssh \
    tmux

ENTRYPOINT ["tmux"]
