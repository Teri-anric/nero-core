### Core Architecture Description of Nero

1. **Module Management**:
   - The core manages the configuration of connected modules, loads them, and handles communication between modules through events. Each module operates as an independent process, with the core coordinating their interaction.

2. **Communication and Integration**:
   - Modules interact with the core via API calls or WebSockets. Additionally, modules can be executed through `dll`, `so`, or `jar` files. Each module's configuration specifies how it should interact with the core.

3. **Data Protocols**:
   - The core includes a repository for protocols that define the data exchange structure between modules in JSON format. Protocols are added along with modules during installation and are used to validate compatibility and ensure proper interaction between modules.

4. **Events and Triggers**:
   - The core supports event handling, where events can be triggered by modules. Events can prompt actions in other modules or initiate specific processes based on the core configuration. This allows for flexible system reactions to changes.

5. **Updates and Compatibility**:
   - When a module requires a protocol update, the new version is added only if it's compatible with the old one. In case of incompatibility, an event is triggered, which is processed by the UI module to allow user interaction.

6. **Error Handling**:
   - In the event of errors during module execution, the core logs the error. The module configuration can define an error-handling policy, such as retrying the execution in case of failure.

7. **Module Classification**:
   - Modules are tagged with labels that indicate their type or function. This simplifies their identification, classification, and interaction configuration within the system.
