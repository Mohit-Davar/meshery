---
layout: default
title: Relationships
permalink: concepts/logical/relationships
type: concepts
abstract: "Meshery Relationships identify and facilitate genealogy between Components."
language: en
list: include
redirect_from:
  - concepts/relationships
---

Meshery Relationships characterize how [components](./components) are connected and interact with each other. Relationships are defined within [models](./models) to aid in structuring the interrelationships between one or more components in a [design](./designs) to further in comprehending the overall structure and dependencies within managed systems.

Meshery recognizes that relationships exist in various forms and that the existence of a relationship might be interdependent upon the existence (or absence) of another relationship. To support this complexity, Meshery relationships are highly expressive, characterizing the nature of interaction of interconnected components no matter their genealogy.

**Benefits of Using Meshery Relationships**

- **Improved Visibility:** Relationships provide a clear visual representation of the connections between components, making it easier to understand the system's architecture.
- **Enhanced Design:** Relationships help you make informed decisions about component selection and placement, leading to better design choices.
- **Automated Configuration:** Relationship-driven actions can automate the configuration of components, reducing manual effort and potential errors.
- **Increased Flexibility:** The use of selectors, actions, and operators provides flexibility in defining and managing relationships.

{% include/alert.html type="dark" title="Contributor Guide to Meshery Relationships" content="If you want to create a new relationship definition or modify existing relationship definitions, see the <a href='https://docs.meshery.io/project/contributing/contributing-relationships'>Contributing to Meshery Relationships</a> guide." %}

## Types of Relationships

Meshery supports different types of relationships to cater to various use cases:

- **Hierarchical Relationships:** These represent parent-child relationships between components, where one component is a dependency of another. arent-child relationships show clear lineage, similar to a family tree (child, parent, grandparent, etc.).
- **Sibling Relationships:** These represent relationships between components that are not directly dependent on each other but may still interact or influence each other's behavior; they describe components that share a common origin but operate independently (siblings, cousins, etc.).
- **Edge Relationships:** These represent relationships that are visually depicted as edges connecting components in MeshMap. Edge relationships are used to define how components interact with each other, such as network connections, bindings, or permissions. They are also used to identify interdependencies between components.
- **TagSets Relationships:** These represent relationships between components of same Labels or Annotations key/value pairs. Labels and Annotations are two different types of Tags. Labels are often used to identify components and are visible on the design canvas. Annotations are often used to provide additional information about components.
 
Relationships are are categorized into different kinds, types, and subtypes, so that can be expressive of the specific manner in which one or more components relate to one another. Each type of relationship can be interpretted by Meshery UI (or other [extensions](/extensibility/extensions)) and mapped to a specific visual paradigm for the given kind relationship. Let's look at some examples of these visual paradigms; let's explore examples of way in which relationships are represented in Meshery.


<!-- Broadly, here is a list of the different types of relationships that Meshery supports:

1. Edge
   1. Network
      1. Firewall
      2. Load Balancer
      3. Ingress
   2. Binding
      1. Mount
      2. Permission
2. Heirarchical
   1. Inventory
   2. Parent 
3. TagSets -->

{% include relationships.html %}

## The Meaning of Relationships

Meshery supports a variety of relationships between components. These relationships are categorized into two types: Semantic and Non-Semantic. Relationships are categorized by whether they are meaningful in terms of how Meshery manages entities - a Semantic relationship - or are simply annotations to aid in the comprehension of you as the designer of the relationship - a Non-Semantic relationship.

### Semantic Relationships

Semantic relationships are those that are meaningful in the context of the application or infrastructure. For example, a `Service` in Kubernetes is semantically related to a `Deployment` or a `Pod`. These relationships are meaningful and are managed by Meshery.

### Non-Semantic Relationships

Non-semantic relationships are those that are meaningful to you as a user and your mental representation of your infrastructure and applications, but are not meaningful in terms of how Meshery evaluates the design or manages these relationships and their associated components. Non-sematic relationships are ignored by Meshery's lifecycle management engine. For example, a `Rectangle` shape that encloses other components (has a parent relationship with other child components) is not semantically meaningful to the way in which Meshery manages these resources. While the `Rectangle` shape might have a parent-child relationship with any number of Meshery-managed components, such a relationship does not implicate any management that Meshery might perform; they are not managed by Meshery.

<!-- @iArchitSharma, help, if you would please.

_[TODO: a visual example is needed here]_ -->

#### Identifiying Non-Semantic Relationships

The `isAnnotation` attribute of a Relationship or Component determines whether the given Relationship or Component represents a management concern for Meshery; whether the given Relationship or Component is sematically meaningful, and whose lifecycle is managed by Meshery.

## Core Concepts of Relationships

- Kinds
- Types
- Subtypes
- Selectors
- Selectors Sets

## Kind, Type, and Subtype of Relationships

The combination of `kind`, `type`, and `subType` uniquely determines the visual paradigm for a given relationship; i.e., relationships with the same `kind`, `type`, and `subType` will share an identical visual representation regardless of the specific components involved in the relationship.

### 1. Edge - Network

This Relationship type configures the networking between one or more components.

**Examples**: An edge-network relationship between a Service and a Deployment or an edge-binding relationship between an Ingress and a Service.

- Example 1) Service --> Deployment
- Example 2) IngressController --> Ingress --> Service

<details close><summary>Visual Representation of Edge-Network Relationships</summary>
           <br>
           <figure><figcaption>1. Edge - Network: Ingress to Service<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=1f79b0c6-2efe-4ee9-b08c-e1bd07a3926b"> (open in playground)</a></figcaption>
           <img alt="Edge - Network" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_network_ingress_to_service_relationship.svg"/>
           </figure>
           <figure><figcaption>2. Edge - Network: Service to Pod<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=90a9b4a0-a296-44b5-b1c5-7b1cb4827a77"> (open in playground)</a></figcaption>
           <img alt="Edge - Network: Ingress to Service" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_network_service_to_pod_relationship.svg"/>
           </figure>
           <figure><figcaption>3. Edge - Network: Service to Service<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=4e368e07-5039-400e-b637-96b0241af799"> (open in playground)</a></figcaption>
           <img alt="Edge - Network" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_network_service_to_service_relationship.svg"/>
           </figure>
           <figure><figcaption>4. Edge - Network: Service to Endpoint<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=ab35416d-7cf7-4540-8b2e-7271ffeadde2"> (open in playground)</a></figcaption>
           <img alt="Edge - Network" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_network_service_to_endpoints_relationship.svg"/>
           </figure>
           <figure><figcaption>5. Edge - Network: Service to Deployment<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=33742281-428d-4340-b42e-6a0fd4ba1d0a"> (open in playground)</a></figcaption>
           <img alt="Edge - Network" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/network_edge_relationship_service_deployment.svg"/>
           </figure>
   </details>

### 2. Edge - Mount

**Example**: Assignment of PersistentVolumes to Pods via PersistenVolumeClaim.

- Example 1) Pod --> PersistenVolumeClaim --> PersistentVolume

<details close><summary>Visual Representation of Edge-Mount Relationship</summary>
           <br>
           <p>Edge - Mount: Pod and Persistent volume via Persistent volume claim<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=43d5fdfe-25f8-4c2c-be9d-30861bbc2a08"> (open in playground)</a> </p>
           <figure>
           <img alt="Edge - Mount" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_mount_relationship_pod_persistent_volume.svg"/>
           </figure>
   </details>

### 3. Edge - Permission

**Example**: The set of Service Accounts that are entitled with the one or more Roles/ClusterRoles bound via Role/ClusterRoleBinding.

- Example 1) ClusterRole --> CluserRoleBinding --> ServiceAccount
- Example 2) Role --> RoleBinding --> ServiceAccount

<details close><summary>Visual Representation of Edge-Permission Relationship</summary>
           <br>
           <figure><figcaption>1. Edge - Permission: Cluster Role to Service Account <a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=27454352-6b1b-426e-830e-683b8c34b94e"> (open in playground)</a></figcaption>
           </figure>
<div id="embedded-design-a7b22d89-41bc-4379-a983-20e835341faf" style="height:30rem;width:100%;"></div>
<script src="{{ site.baseurl }}/assets/img/meshmodel/relationships/embedded-design-edge-binding-permissions-relationship.js" type="module" ></script>
</details>

### 4. Edge - Firewall

Kubernetes Network Policy for controlling ingress and egress traffic from Pod-to-Pod

- Example 1) Pod --> NetworkPolicy --> Pod

<details close><summary>Visual Representation of Edge-Firewall Relationship</summary>
           <br>
           <figure><figcaption>Edge - Firewall: Pod to Pod<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=58fda714-eaa4-490f-b228-b8bcfe3a1e47s"> (open in playground)</a></figcaption>
           <img alt="Edge - Firewall" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/edge_firewall_relationship_pod_to_pod.svg">
           </figure>
   </details>

### 5. Edge - Reference

Logical or declarative links between components where one component refers to another by name, identifier, type, or scope.

- Example 1) Pod --> ConfigMap (via envFrom)
- Example 2) Pod --> Secret (via volumes)

<details close><summary>Visual Representation of Edge-Reference Relationship</summary>
        <br>
        <p>The <strong>Edge-Reference</strong> relationship type represents a <strong>logical or declarative link</strong> between two components, where one component <strong>refers to another by name, identifier, type, or scope</strong>. This relationship allows components to dynamically locate, associate with, or depend on other components without being tightly coupled to them. It forms the basis for indirect communication, configuration reuse, ownership tracking, and dependency resolution in distributed systems.</p>
        <p>This type of relationship does <strong>not directly provide communication, access, or permission</strong>, but <strong>enables such interactions by declaring intent or pointing to another component</strong>.</p>
        <br>
           <figure><figcaption>Edge - Reference: Pod to ConfigMap and Secret<a target="_blank" href="https://kanvas.new/extension/meshmap?mode=design&design=8288ffad-c406-4129-94b1-86f044ef1ccb"> (open in playground)</a></figcaption>
           </figure>
<div id="embedded-design-8288ffad-c406-4129-94b1-86f044ef1ccb" style="height:30rem;width:100%;"></div>
<script src="{{ site.baseurl }}/assets/img/meshmodel/relationships/embedded-design-edge-reference.js" type="module" ></script>
   </details>

### 6. Hierarchical - Parent - Wallet

**Example**

- Example 1) (binary and configuration) --> IstioWASMPlugin
- Example 2) WASMFilter (binary and configuration) --> IstioEnvoyFilter

<details close><summary>Visual Representation of Hierarchical-Inventory Relationship</summary>
           <figure><br><figcaption>1. Hierarchical - Inventory: Namespace and ConfigMap<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=7d3107fb-c0fe-43cb-9729-cf1674e5d1af"> (open in playground)</a></figcaption>
           </figure>
<div id="embedded-design-d0987b9a-b20e-4bc1-b47c-69ca3078d380" style="height:30rem;width:100%;"></div>
<script src="{{ site.baseurl }}/assets/img/meshmodel/relationships/embedded-design-hierarchical-parent-wallet-relationship.js" type="module" ></script>
</details>

### 7. Hierarchical - Parent - Inventory

**Example**:

- Example 1) Any namespaced Kubernetes component --> Kubernetes Namespace

<details close><summary>Visual Representation of Hierarchical-Parent Relationship</summary>
           <figure><br><figcaption>1. Hierarchical - Parent: Namespace (Parent) and ConfigMap (child), Role (Child) <a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=ccf38fba-6ada-4332-8ee7-033ee2c21f91"> (open in playground)</a></figcaption>
           </figure>
<div id="embedded-design-ccf38fba-6ada-4332-8ee7-033ee2c21f91" style="height:30rem;width:100%;"></div>
<script src="{{ site.baseurl }}/assets/img/meshmodel/relationships/embedded-design-hierarchical-parent-inventory-relationship.js" type="module" ></script>
</details>

### 8. Match - Labels (Tagsets)

This relationship type defines the associations between components based on shared Labels or Annotations.

**Example**: An label-based tag-set relationship between a NodePort service and an application. 

<details close><summary>Visual Representation of Tag-Sets Relationship</summary>
          <br>
          <figure><figcaption>Tag-Set: Service and Deployment that share the same label<a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=2d0a36b9-8170-4076-8aea-4fa6b28caf31"> (open in playground)</a></figcaption>
          <img alt="Edge - Firewall" src="{{ site.baseurl }}/assets/img/meshmodel/relationships/tagset_relationship.svg"/>
          </figure>        
</details>

### 9. Edge - Annotation 

This relationship depicts connections between components without conveying specific semantic meaning.

**Example**: Demonstration of connections between AWS components.

<details close><summary>Visual Representation of Edge - Annotation Relationship</summary>
           <figure><br><figcaption>Edge - Annotation: Relationship between AWS components <a target="_blank" href="https://playground.meshery.io/extension/meshmap?mode=design&design=daecd14f-6c65-45d9-b74a-4fc536a7868f"> (open in playground)</a></figcaption>
           </figure>
<div id="embedded-design-daecd14f-6c65-45d9-b74a-4fc536a7868f" style="height:30rem;width:100%;"></div>
<script src="{{ site.baseurl }}/assets/img/meshmodel/relationships/embedded-design-edge-annotation-relationship.js" type="module" ></script>
</details>

## Selectors in Relationships

In Meshery, a selector is a way to specify which set of components a certain other component should affect or interact with. Selectors provide a flexible and powerful way to manage and orchestrate resources within a under Meshery's management.

Selectors can be applied to various components, enabling a wide range of relationship definitions. Here are some examples:

<table class="table table-dark table-active">
    <tr>
        <th>Model Component</th>
        <th>Relationship Kind</th>
        <th>Relationship SubType</th>
        <th>Model Component</th>
    </tr>
    <tr>
        <td>Kubernetes ConfigMap</td>
        <td>Hierarchical</td>
        <td>Inventory</td>
        <td>Kubernetes Pod</td>
    </tr>
    <tr>
        <td>Kubernetes ConfigMap</td>
        <td>Hierarchical</td>
        <td>Inventory</td>
        <td>Kubernetes Deployment</td>
    </tr>
    <tr>
        <td>Meshery WASMFilter</td>
        <td>Hierarchical</td>
        <td>Inventory</td>
        <td>Istio EnvoyFilter</td>
    </tr>
</table>

The above relationships pairs have hierarchical inventory relationships, and visual paradigm remain consistent across different components. A snippet of the selector backing this relationship is listed below.
<details>
<summary>Example Relationship Selector</summary>
<code><pre>
"selector": {
    "allow": {
        "from": [
          {
            "kind": "ConfigMap",
            "model": "kubernetes",
            "patch": {
              "patchStrategy": "replace",
              "mutatorRef": [
                [
                  "name"
                ]
              ],
              "description": "In Kubernetes, ConfigMaps are a versatile resource that can be referenced by various other resources to provide configuration data to applications or other Kubnernetes resources.\n\nBy referencing ConfigMaps in these various contexts, you can centralize and manage configuration data more efficiently, allowing for easier updates, versioning, and maintenance of configurations in a Kubernetes environment."
            }
          }
        ],
        "to": [
          {
            "kind": "Pod",
            "model": "kubernetes",
            "patch": {
              "patchStrategy": "replace",
              "mutatedRef": [
                [
                  "settings",
                  "spec",
                  "containers",
                  "_",
                  "envFrom",
                  "0",
                  "configMapRef",
                  "name"
                ]
              ],
              "description": "ConfigMaps can be referenced in the Pod specification to inject configuration data into the Pod's environment.\n\nThe keys from the ConfigMap will be exposed as environment variables to the container within the Pod."
            }
          }
        ]
    }
}
</pre></code>

</details>

The above snippet defines a selector configuration for allowing relationships between `Kubernetes ConfigMap` and `Kubernetes Pod`.

 <!-- add images -->

## Relationship Evaluation

Meshery employs a policy-driven approach to evaluate relationships between components. This evaluation helps in:

- Determining compatible components for establishing relationships
- Suggesting potential relationships based on the current design
- Validating existing relationships and identifying potential conflicts
- Automating the configuration of components based on established relationships


Each invocation of the evaluation process attempts to recursively evaluate the design until it reaches a stable state—i.e., no further changes are detected. If a bug in the evaluation policies causes non-terminating behavior (such as endlessly generating new components), the evaluation will be forcibly stopped after a configurable maximum depth (e.g., 5 iterations), and an error will be raised.

During evaluation, in addition to the input design, the evaluation engine has access to all relationships stored in the registry. These relationships serve as the source of truth for policies to validate existing relationships  or identify new ones. Since relationships can be associated with different models, not all of them are relevant to a given design. To ensure efficiency, the evaluation process intelligently filters the registered relationships, retaining only those that directly impact the design.


Currently, the filtering logic includes only relationships from models that are already part of the design. For example, if the design consists solely of Kubernetes components, relationships from the AWS model will not be loaded for evaluation.

Beyond this automatic filtering, relationship evaluation can also be selectively disabled within the design. This is achieved by setting preferences to false for specific relationship categories, defined by their kind, type, and subtype.

![Meshery Relationship](/assets/img/concepts/logical/relationship-evaluation-flow.svg)

### How Relationships are formed?

1. You can create relationships manually by using the edge handles, bringing related components to close proximity or dragging a component inside other component. It may happen that, you created a relationship from the UI, but the <a href='/concepts/logical/policies'>Policy Engine</a> rejected or overrode the decision if all the constraints for a particular relationship are not satisfied.

2. Relationships are automatically created when a component's configuration is modified in a way that relationship criteria is satisfied.

{% include/alert.html type="info" title="Explore an example relationship" content="To explore an example of this behavior, see the <a href='https://meshery.io/catalog/deployment/example-edge-permission-relationship-7dd39d30-7b14-4f9f-a66c-06ba3e5000fa.html'>Example Edge-Permission Relationship</a> and follow the steps written in its description." %}

When the relationships are created by the user, almost in all cases the config of the involved components are patched. To see the specific of patching refer [Patch Strategies](#patch-strategies).

Designs are evaluated by the [Policy Engine]({{site.baseurl}}/concepts/logical/policies) for potential relationships.

<!-- Explain how and what configs get patched when relationships are created -->
<!-- Explain real time evaluationof relationships on -->
<!-- 1. Import -->
<!-- 2. When compoennt config is update and it statisfied the condition for the relationship -->

### Patch Strategies

Patches in Meshery relationships utilize strategies and references (mutatorRef/mutatedRef) for the from and to fields. These convey the property path that will be updated as the relationship is created.

### Caveats and Considerations

1. If the user creates a `Hierarchical Inventory` relationship between `Pod`, `Job`, and any other high-level Kubernetes resources like `Deployment`, `StatefulSet`, or `CronJobs`, after the relationship has been established unfortunately, there's no system to remove the extra pod configuration automatically.
If the design is not configured with `labels` `selectors` and `replicas` appropriately, there's a possibility of additional resources getting provisioned when deployed. eg: The relationship between a Pod and deployment can result in 2 Pods (1 pod coming as part of deployment resource) and 1 Deployment.  It's important to be aware of this possibility and manage configurations carefully to avoid unexpected issues during deployment

# Itemizing your Relationship Definitions in your Meshery deployment

In any given Meshery deployment, you can reference and search the full set of registered relationships (in Meshery's internal registry) in using either of Meshery's client interfaces.

**Meshery UI**

- Visit _Setttings_ --> _Registry_

**Meshery CLI**

- Run `mesheryctl relationship list`

<!--
```
mesheryctl model import -f [ oci:// | file:// ]`
``` -->
