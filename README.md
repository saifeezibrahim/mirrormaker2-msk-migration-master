# 🚀 MirrorMaker2 + AWS MSK Migration Lab — Learning Edition

> **A complete, hands-on repo for mastering Apache Kafka migrations to Amazon MSK with MirrorMaker2. Build, test, and understand real-world streaming data migration!**

---

## 🌟 What is This Project?

This repository is your practical playground for learning:
- How to migrate from a self-managed Apache Kafka cluster to Amazon MSK
- How to use **Kafka MirrorMaker2 (MM2)** for topic, config, and ACL replication
- How to keep consumer group offsets in sync across clusters
- How to customize replication policy for seamless topic migration

All resources are designed to accompany the [Amazon MSK migration lab](https://amazonmsk-labs.workshop.aws/en/migration.html), but you can use them standalone to build your streaming data and AWS skills.

---

## 🗂️ What's in the Repo?

```plaintext
README.md                       # This learning guide
CFTemplates/                    # AWS CloudFormation templates for infrastructure
Configuration/                  # Kafka & MM2 configuration files
CustomMM2ReplicationPolicy/     # Custom Java code for replication policy
MM2GroupOffsetSync/             # Java code for syncing consumer group offsets
pom.xml                         # Build and dependency management for Java apps
LICENSE, CODE_OF_CONDUCT.md, CONTRIBUTING.md
```
👉 [Browse all files in GitHub](https://github.com/saifeezibrahim/mirrormaker2-msk-migration-master/tree/main)

---

## 🏗️ Lab Structure

- **CustomMM2ReplicationPolicy**  
  Java implementation that allows you to replicate topics to MSK **without** changing their names (overriding default behavior).  
  _Learn how to customize MirrorMaker2 for your migration needs!_

- **MM2GroupOffsetSync**  
  Tool to sync consumer offsets from source to destination for seamless failover.  
  _Practice running offset syncs and understand consumer group behavior during migration._

- **CloudFormation Templates**  
  Fast-track your infrastructure setup for labs or production alike.

---

## 🚦 Quick Start: Build & Run

### 1. **Clone and Build Java Components**
```bash
git clone https://github.com/saifeezibrahim/mirrormaker2-msk-migration-master.git
cd mirrormaker2-msk-migration-master
mvn clean install -f pom.xml
```
_JARs will be built for CustomMM2ReplicationPolicy and MM2GroupOffsetSync._

### 2. **Use in Your Migration Lab**

#### Run MM2GroupOffsetSync with Help
```bash
java -jar MM2GroupOffsetSync-1.0-SNAPSHOT.jar -h
```

#### Example: Using a Custom Replication Policy
```bash
java -jar MM2GroupOffsetSync-1.0-SNAPSHOT.jar \
  -cgi mm2TestConsumer1 \
  -src msksource \
  -pfp /tmp/kafka/consumer.properties_sync_dest \
  -mtls \
  -rpc com.amazonaws.kafka.samples.CustomMM2ReplicationPolicy
```

#### Example: Using the Default Replication Policy
```bash
java -jar MM2GroupOffsetSync-1.0-SNAPSHOT.jar \
  -cgi mm2TestConsumer1 \
  -src msksource \
  -pfp /tmp/kafka/consumer.properties_sync_dest \
  -mtls
```

---

## 🧑‍💻 What You'll Learn

- How MirrorMaker2 replicates topics, configs, and ACLs between clusters
- The role of **ReplicationPolicy** and how customizing it supports migration or DR
- How to keep consumer group offsets in sync for smooth failovers
- Best practices for Kafka-to-MSK migrations (with or without topic renaming)

---

## 💡 Tips for Learners

- Study the code in `CustomMM2ReplicationPolicy/` to see how to override Kafka replication behavior.
- Try modifying topic patterns and observe the effect on replication.
- Use the CloudFormation templates to quickly create lab infrastructure in AWS.
- Experiment with breaking and fixing syncs to understand failure scenarios.

---

## 🙋‍♂️ Maintained by Saifee Ibrahim

Questions? Ideas? Found this helpful?  
⭐ Star the repo, open issues, or contribute — this lab is built for hands-on AWS and Kafka learning!

---

## 📄 License

MIT — Free for learning and educational use.

---

> **Practice, experiment and master streaming migrations with MirrorMaker2 and AWS MSK!**
