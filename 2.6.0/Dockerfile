# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

## yeongeon/hadoop:2.6.0
FROM yeongeon/centos:6.6
MAINTAINER "Yeongeon KIM" <yeongeon@gmail.com>

# Snappy
RUN yum install -v -y snappy snappy-devel

# Hadoop
WORKDIR /tmp
RUN git clone --branch release-2.6.0 https://github.com/apache/hadoop.git hadoop_src \
  && cd /tmp/hadoop_src \
  && mvn install -Pnative -Pdist -DskipTests=true \
    -Dbundle.snappy=true -Drequire.snappy=true \
  && mv /tmp/hadoop_src/hadoop-dist/target/hadoop-2.6.0 /usr/local/hadoop \
  && rm -rf /tmp/hadoop_src

# Env
ENV HADOOP_HOME=/usr/local/hadoop

RUN echo 'HADOOP_HOME="/usr/local/hadoop"'	>> /etc/environment 
