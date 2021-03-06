# Change Log

## [0.7.0-rc.0](https://github.com/appscode/stash/tree/0.7.0-rc.0) (2018-02-20)
[Full Changelog](https://github.com/appscode/stash/compare/0.6.4...0.7.0-rc.0)

- Implement offline backup for multiple replica [\#335](https://github.com/appscode/stash/pull/335)
- Don't block deletion of owner by default [\#342](https://github.com/appscode/stash/pull/342)
- Skip generating UpdateStatus method [\#341](https://github.com/appscode/stash/pull/341)
- Remove internal types [\#340](https://github.com/appscode/stash/pull/340)
- Use rbac/v1 apis [\#339](https://github.com/appscode/stash/pull/339)
- Add user roles [\#338](https://github.com/appscode/stash/pull/338)
- Use restic 0.8.2 [\#337](https://github.com/appscode/stash/pull/337)
- Use official code generator scripts [\#336](https://github.com/appscode/stash/pull/336)
- Update charts to support api registration [\#334](https://github.com/appscode/stash/pull/334)
- Fix e2e tests after webhook merger [\#333](https://github.com/appscode/stash/pull/333)
- Ensure stash can be run locally [\#332](https://github.com/appscode/stash/pull/332)
- Vendor client-go auth pkg [\#331](https://github.com/appscode/stash/pull/331)
- Update Grafana dashboard [\#330](https://github.com/appscode/stash/pull/330) ([galexrt](https://github.com/galexrt))
- Merge admission webhook and operator into one binary [\#329](https://github.com/appscode/stash/pull/329)
- Merge uninstall script into the stash.sh script [\#328](https://github.com/appscode/stash/pull/328)
- Implement informer factory for backup scheduler [\#325](https://github.com/appscode/stash/pull/325)
- Fixed abnormal pod recreation when Restic is deleted [\#322](https://github.com/appscode/stash/pull/322)
- Copy generic-admission-server into pkg [\#318](https://github.com/appscode/stash/pull/318)
- Use shared infromer factory [\#317](https://github.com/appscode/stash/pull/317)
- Use GetBaseVersion method from kutil [\#316](https://github.com/appscode/stash/pull/316)
- Implement Pause Restic [\#315](https://github.com/appscode/stash/pull/315)
- Fix webhook command description [\#314](https://github.com/appscode/stash/pull/314)
- Use rbac/v1beta1 api. [\#313](https://github.com/appscode/stash/pull/313)
- Support Create & Update operations in admission webhook [\#312](https://github.com/appscode/stash/pull/312)
- Merge webhook plugins into one. [\#311](https://github.com/appscode/stash/pull/311)
- Support private docker registry in installer [\#310](https://github.com/appscode/stash/pull/310)
- Compress go binaries [\#309](https://github.com/appscode/stash/pull/309)
- Rename --initializer flag to --enable-initializer [\#308](https://github.com/appscode/stash/pull/308)
- Remove STASH\_ROLE\_TYPE from installer scripts [\#307](https://github.com/appscode/stash/pull/307)
- Use rbac/v1 api [\#306](https://github.com/appscode/stash/pull/306)
- Use kubectl auth reconcile [\#305](https://github.com/appscode/stash/pull/305)
- Add --initializer flag to installer [\#304](https://github.com/appscode/stash/pull/304)
- Prepare docs for 0.7.0-alpha.0 [\#302](https://github.com/appscode/stash/pull/302)
- Change installer script [\#301](https://github.com/appscode/stash/pull/301)
- Added support for private docker registry [\#300](https://github.com/appscode/stash/pull/300)
- Add ValidatingAdmissionWebhook for Stash CRDs [\#299](https://github.com/appscode/stash/pull/299)
- Remove TPR to CRD migrator [\#298](https://github.com/appscode/stash/pull/298)
- Update dependencies to Kubernetes 1.9 [\#297](https://github.com/appscode/stash/pull/297)
- Write restic stderror in error events [\#296](https://github.com/appscode/stash/pull/296)
- Fixed backup count [\#295](https://github.com/appscode/stash/pull/295)
- Support self-signed ca cert for backends [\#294](https://github.com/appscode/stash/pull/294)


## [0.6.4](https://github.com/appscode/stash/tree/0.6.4) (2018-02-20)
[Full Changelog](https://github.com/appscode/stash/compare/0.6.3...0.6.4)

- Update docs for 0.6.4 [\#344](https://github.com/appscode/stash/pull/344)
- Don't block deletion of owner by default [\#343](https://github.com/appscode/stash/pull/343)


## [0.6.3](https://github.com/appscode/stash/tree/0.6.3) (2018-01-18)
[Full Changelog](https://github.com/appscode/stash/compare/0.6.2...0.6.3)

- Add Stash Backup Grafana dashboard to monitoring docs [\#285](https://github.com/appscode/stash/issues/285)
- Added Grafana Stash overview dashboard [\#286](https://github.com/appscode/stash/pull/286) ([galexrt](https://github.com/galexrt))
- PushGateURL not given to sidecar container [\#283](https://github.com/appscode/stash/issues/283)
- Fix inline volumeSource marshalling for LocalSpec [\#289](https://github.com/appscode/stash/pull/289)
- Verbosity \(--v\) flag not inherited to backup sidecars [\#282](https://github.com/appscode/stash/issues/282)
- Fixed parsing argument error [\#291](https://github.com/appscode/stash/pull/291)


## [0.6.2](https://github.com/appscode/stash/tree/0.6.2) (2018-01-05)
[Full Changelog](https://github.com/appscode/stash/compare/0.6.1...0.6.2)

- Created stash-sidecar clusterrole is missing statefulsets permission [\#272](https://github.com/appscode/stash/issues/272) ([galexrt](https://github.com/galexrt))
- Fix RBAC roles in chart [\#276](https://github.com/appscode/stash/pull/276)
- Garbage collect service-accounts and role-bindings for jobs [\#275](https://github.com/appscode/stash/pull/275)
- Fix new restic format in upgrade docs [\#274](https://github.com/appscode/stash/pull/274)
- Add statefulsets to stash-sidecar ClusterRole creation [\#273](https://github.com/appscode/stash/pull/273) ([galexrt](https://github.com/galexrt))
- Update Helm chart to use newer 'fullname' template that avoids duplicate \(e.g. 'stash-stash-...'\) resource names [\#277](https://github.com/appscode/stash/pull/277) ([whereisaaron](https://github.com/whereisaaron))
- Reduce operator permissions for service accounts [\#270](https://github.com/appscode/stash/pull/270)
- Fix formatting of uninstall.md [\#269](https://github.com/appscode/stash/pull/269)


## [0.6.1](https://github.com/appscode/stash/tree/0.6.1) (2018-01-03)
[Full Changelog](https://github.com/appscode/stash/compare/0.6.0...0.6.1)

- Image kubectl not found because of Kubernetes version [\#266](https://github.com/appscode/stash/issues/266)


## [0.6.0](https://github.com/appscode/stash/tree/0.6.0) (2018-01-03)
[Full Changelog](https://github.com/appscode/stash/compare/0.4.2...0.6.0)

- Reorganize docs [\#263](https://github.com/appscode/stash/pull/263)
- Add support for B2 [\#262](https://github.com/appscode/stash/pull/262)
- Update restic website link [\#261](https://github.com/appscode/stash/pull/261)
- Update docs for unified LocalSpec [\#260](https://github.com/appscode/stash/pull/260)
- Unify LocalSpec and RecoveredVolume [\#259](https://github.com/appscode/stash/pull/259)
- Remove restic-dependency from recovery [\#258](https://github.com/appscode/stash/pull/258)
- Update restic version to 0.8.1 [\#257](https://github.com/appscode/stash/pull/257)
- Use cmp methods from kutil [\#255](https://github.com/appscode/stash/pull/255)
- Remove TryPatch methods [\#254](https://github.com/appscode/stash/pull/254)
- Log operator version on start [\#253](https://github.com/appscode/stash/pull/253) ([galexrt](https://github.com/galexrt))
- Use verb type for mutation [\#251](https://github.com/appscode/stash/pull/251)
- Use CreateOrPatchCronJob from kutil [\#250](https://github.com/appscode/stash/pull/250)
- Indicate mutation in PATCH helper method return [\#249](https://github.com/appscode/stash/pull/249)
- Simplify clientID generation for analytics [\#247](https://github.com/appscode/stash/pull/247)
- Set analytics clientID [\#246](https://github.com/appscode/stash/pull/246)
- Upgrade procedure for 0.5.1 to 0.6.0 [\#243](https://github.com/appscode/stash/pull/243)
- Fix retentionPolicyName not found error [\#242](https://github.com/appscode/stash/pull/242)
- Enable Restic cahce-dir flag [\#241](https://github.com/appscode/stash/pull/241)
- Use lower case workload.kind in prefix [\#240](https://github.com/appscode/stash/pull/240)
- Use RegisterCRDs helper [\#239](https://github.com/appscode/stash/pull/239)
- Implement offline backup [\#229](https://github.com/appscode/stash/pull/229)
- Run `restic check` once every 3 days [\#223](https://github.com/appscode/stash/pull/223)
- Record recovery status for individual FileGroup [\#222](https://github.com/appscode/stash/pull/222)
- PollInfinitely for recovery job to succeed
- Dynamically create stash-sidecar ClusterRole in operator [\#221](https://github.com/appscode/stash/pull/221)
- Implement workload initializer in stash operator [\#207](https://github.com/appscode/stash/pull/207)
- Leader election for deployment, replica set and rc [\#206](https://github.com/appscode/stash/pull/206)
- Implement Recovery for Restic Backup [\#202](https://github.com/appscode/stash/pull/202)
- Make stash chart namespaced [\#210](https://github.com/appscode/stash/pull/210)
- Use client-go 5.0 [\#203](https://github.com/appscode/stash/pull/203)
- Add recovery CRD [\#201](https://github.com/appscode/stash/pull/201)


## [0.4.2](https://github.com/appscode/stash/tree/0.4.2) (2017-11-03)
[Full Changelog](https://github.com/appscode/stash/compare/0.5.1...0.4.2)

- Fix RBAC permission for release 0.4 [\#208](https://github.com/appscode/stash/pull/208)
- Upgrade restic binary to 0.7.3 [\#209](https://github.com/appscode/stash/pull/209)


## [0.5.1](https://github.com/appscode/stash/tree/0.5.1) (2017-10-10)
[Full Changelog](https://github.com/appscode/stash/compare/0.5.0...0.5.1)

- Correctly detect "default" service account [\#200](https://github.com/appscode/stash/pull/200)
- Clarify that --tag foo,tag bar style tags are not supported. [\#199](https://github.com/appscode/stash/pull/199)
- Set hostname based on resource type [\#198](https://github.com/appscode/stash/pull/198)
- Manage RoleBinding for rbac enabled cluster [\#197](https://github.com/appscode/stash/pull/197)
- Document how to detect operator version [\#196](https://github.com/appscode/stash/pull/196)


## [0.5.0](https://github.com/appscode/stash/tree/0.5.0) (2017-10-10)
[Full Changelog](https://github.com/appscode/stash/compare/0.5.0-beta.3...0.5.0)

- Fix e2e tests [\#183](https://github.com/appscode/stash/pull/183)
- Use workqueue [\#182](https://github.com/appscode/stash/pull/182)
- Use Deployment from apps/v1beta1 [\#181](https://github.com/appscode/stash/pull/181)
- Delete \*.generated.go files for ugorji [\#180](https://github.com/appscode/stash/pull/180)
- Use WaitForCRDReady from kutil [\#179](https://github.com/appscode/stash/pull/179)
- Only watch apps/v1beta1 Deployment [\#178](https://github.com/appscode/stash/pull/178)
- Move kutil to client package [\#177](https://github.com/appscode/stash/pull/177)
- Generate ugorji stuff [\#176](https://github.com/appscode/stash/pull/176)
- Prepare docs for 0.5.0 [\#174](https://github.com/appscode/stash/pull/174)
- Install stash as a critical addon [\#173](https://github.com/appscode/stash/pull/173)
- Set RESTIC\_VER to 0.7.3 [\#172](https://github.com/appscode/stash/pull/172)
- Refresh charts to match recent convention [\#171](https://github.com/appscode/stash/pull/171)
- Update kutil [\#170](https://github.com/appscode/stash/pull/170)
- Fix deployment name in tutorial [\#169](https://github.com/appscode/stash/pull/169)
- Fix command in Developer-guide [\#168](https://github.com/appscode/stash/pull/168)
- Use apis/v1alpha1 instead of internal version [\#167](https://github.com/appscode/stash/pull/167)


## [0.4.1](https://github.com/appscode/stash/tree/0.4.1) (2017-07-19)
[Full Changelog](https://github.com/appscode/stash/compare/0.4.0...0.4.1)

- Fixes [robfig/cron bug](https://github.com/robfig/cron/issues/106) that causes multiple invocation of scheduled function.
- Fix Fake restic resource Url (#137)
- Add omitempty for Local storage
- Build binary inside Alpine Docker image.


## [0.4.0](https://github.com/appscode/stash/tree/0.4.0) (2017-07-07)
[Full Changelog](https://github.com/appscode/stash/compare/0.3.1...0.4.0)

- `restic` updated to https://github.com/appscode/restic/tree/stash-0.4.0 . This includes an updated Azure-sdk-fo-go with support for [reading partial blobs](https://github.com/Azure/azure-sdk-for-go/pull/664). This should improve backup speed for Azure backend. The repository URL format is also updated to `gs|azure:container:/[prefix]`.
- `spec.backend.repositorySecretName` is renamed to `spec.backend.storageSecretName`
- `spec.backend.local.Volume` is now a [VolumeSource](https://github.com/kubernetes/api/blob/fbfbec433b66a821a31a83696b308322e5e5dff9/core/v1/types.go#L246) and is renamed to `spec.backend.local.VolumeSource`. When `Local` backend is used, Stash mounts the `local.VoumeSource` with volume name `stash-local`.


## [0.3.1](https://github.com/appscode/stash/tree/0.3.1) (2017-07-04)
[Full Changelog](https://github.com/appscode/stash/compare/0.3.0...0.3.1)

- Add tests for swift [\#130](https://github.com/appscode/stash/pull/130)


## [0.3.0](https://github.com/appscode/stash/tree/0.3.0) (2017-07-04)
[Full Changelog](https://github.com/appscode/stash/compare/0.2.0...0.3.0)

- Fix GCS [\#122](https://github.com/appscode/stash/issues/122)
- Support resource [\#128](https://github.com/appscode/stash/issues/128)
- Document FindRestic will match first one [\#119](https://github.com/appscode/stash/issues/119)
- Document e2e test setup process. [\#108](https://github.com/appscode/stash/issues/108)
- Fix charts [\#87](https://github.com/appscode/stash/issues/87)
- Support setting compute resources for sidecar [\#129](https://github.com/appscode/stash/pull/129)
- Fix RBAC docs [\#127](https://github.com/appscode/stash/pull/127)
- Document swift [\#124](https://github.com/appscode/stash/pull/124)


## [0.2.0](https://github.com/appscode/stash/tree/0.2.0) (2017-06-30)
[Full Changelog](https://github.com/appscode/stash/compare/0.1.0...0.2.0)

- Part 6 - Update docs [\#121](https://github.com/appscode/stash/pull/121)
- Update docs [\#120](https://github.com/appscode/stash/pull/120)
- Various bug fixes [\#118](https://github.com/appscode/stash/pull/118)
- Update pitch [\#117](https://github.com/appscode/stash/pull/117)
- Part 5 - User Guide [\#114](https://github.com/appscode/stash/pull/114)
- Part 4- User Guide [\#113](https://github.com/appscode/stash/pull/113)
- Part 3 - User Guide [\#110](https://github.com/appscode/stash/pull/110)
- Update user guide [\#94](https://github.com/appscode/stash/pull/94)
- Create separate restic for each type of backend. [\#92](https://github.com/appscode/stash/pull/92)
- Remove selectors so that `template.metadata.labels` are used [\#91](https://github.com/appscode/stash/pull/91)
- Update Stash chart [\#89](https://github.com/appscode/stash/pull/89)
- Various changes to RetentionPolicy	 [\#116](https://github.com/appscode/stash/pull/116)
- Set TMPDIR env var for restic [\#115](https://github.com/appscode/stash/pull/115)
- Part - 2 of User guide [\#99](https://github.com/appscode/stash/pull/99)
- Update Prometheus job name to use restic ns & name [\#93](https://github.com/appscode/stash/pull/93)
- Add docs for commands [\#90](https://github.com/appscode/stash/pull/90)
- Fix dev guide [\#88](https://github.com/appscode/stash/pull/88)


## [0.1.0](https://github.com/appscode/stash/tree/0.1.0) (2017-06-27)
**Implemented enhancements:**

- Add e2e tests for major cloud providers [\#84](https://github.com/appscode/stash/pull/84)
- Add /snapshots endpoint in operator [\#82](https://github.com/appscode/stash/pull/82)
- Handle update conflicts [\#78](https://github.com/appscode/stash/pull/78)
- Test e2e tests [\#76](https://github.com/appscode/stash/pull/76)
- Delete old testify tests [\#75](https://github.com/appscode/stash/pull/75)
- Create a cli wrapper for restic [\#74](https://github.com/appscode/stash/pull/74)
- Revise EnsureXXXSidecar methods [\#73](https://github.com/appscode/stash/pull/73)
- Add ginkgo based e2e tests [\#70](https://github.com/appscode/stash/pull/70)
- Push metrics to Prometheus push gateway [\#67](https://github.com/appscode/stash/pull/67)
- Use go-sh to execute restic commands [\#63](https://github.com/appscode/stash/pull/63)
- Add scratchDir & prefixHostname flags [\#62](https://github.com/appscode/stash/pull/62)
- Support remote backends [\#58](https://github.com/appscode/stash/pull/58)
- Organize backup code. [\#54](https://github.com/appscode/stash/pull/54)
- Synchronize scheduler reconfiguration [\#53](https://github.com/appscode/stash/pull/53)
- Fix unit tests [\#51](https://github.com/appscode/stash/pull/51)
- Check docker image tag before starting operator [\#45](https://github.com/appscode/stash/pull/45)
- Expose metrics from operator [\#44](https://github.com/appscode/stash/pull/44)
- Add analytics [\#41](https://github.com/appscode/stash/pull/41) ([aerokite](https://github.com/aerokite))
- Use V1alpha1SchemeGroupVersion for Restik [\#40](https://github.com/appscode/stash/pull/40) ([aerokite](https://github.com/aerokite))
- Fix status update [\#38](https://github.com/appscode/stash/pull/38)
- Upgrade restic version to 0.6.1 [\#37](https://github.com/appscode/stash/pull/37)
- Change api version to v1alpha1 [\#30](https://github.com/appscode/stash/pull/30)
- Rename function and structure [\#29](https://github.com/appscode/stash/pull/29)
- Rename Backup into Restik [\#28](https://github.com/appscode/stash/pull/28)
- Move api from k8s-addons [\#27](https://github.com/appscode/stash/pull/27)
- Bubble up errors to caller [\#26](https://github.com/appscode/stash/pull/26)
- Allow modifying the cron expression [\#25](https://github.com/appscode/stash/pull/25)
- Use unversioned time [\#23](https://github.com/appscode/stash/pull/23)
- Restik chart [\#20](https://github.com/appscode/stash/pull/20)
- example added [\#19](https://github.com/appscode/stash/pull/19)
- Move restik api and client to k8s-addons [\#18](https://github.com/appscode/stash/pull/18)
- Error print fix [\#17](https://github.com/appscode/stash/pull/17)
- Check group registration [\#16](https://github.com/appscode/stash/pull/16)
- Restik docs [\#15](https://github.com/appscode/stash/pull/15)
- Restik unit test, e2e test [\#14](https://github.com/appscode/stash/pull/14)
- Restik create delete initial implementation [\#12](https://github.com/appscode/stash/pull/12)
- Build docker image [\#11](https://github.com/appscode/stash/pull/11)
- Clone skeleton from appscode/k3pc [\#10](https://github.com/appscode/stash/pull/10)
- Fix e2e tests [\#83](https://github.com/appscode/stash/pull/83)
- Mount scratchDir with operator [\#80](https://github.com/appscode/stash/pull/80)
- Fix scheduler  [\#79](https://github.com/appscode/stash/pull/79)
- Create RBAC objects for operator [\#69](https://github.com/appscode/stash/pull/69)
- Mount labels using Downward api [\#66](https://github.com/appscode/stash/pull/66)
- Vendor go-sh dependency [\#65](https://github.com/appscode/stash/pull/65)
- Update e2e tests [\#52](https://github.com/appscode/stash/pull/52)
- Run watchers for preferred api group version kind [\#50](https://github.com/appscode/stash/pull/50)
- Build restic from source by default [\#49](https://github.com/appscode/stash/pull/49)
- Watch individual object types. [\#48](https://github.com/appscode/stash/pull/48)
- Various code cleanup [\#47](https://github.com/appscode/stash/pull/47)
- Reorganize cron controller [\#46](https://github.com/appscode/stash/pull/46)
- Run push gateway as a side-car for restik operator. [\#43](https://github.com/appscode/stash/pull/43)
- Use client-go [\#36](https://github.com/appscode/stash/pull/36)
