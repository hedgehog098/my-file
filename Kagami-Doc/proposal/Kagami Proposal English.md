# Kagami
A distributed mirroring system and management tools. \
The project name "Kagami" is derived from the Japanese word for "mirror". \
More infomation can be found on our website: [Project-Kagami](https://project-kagami.dev)

Powerd by *ProjectSoftoid*

## Group Info
Group Number: 3 \
Group Name: ProjectSoftoid \

## Team Profile
### Team Member:
1. TaoXilin_1220032801, proficient in git, familiar with python, c, cpp, etc., master front-end construction skills, and master knowledge of algorithms and data structures.
2. 2.ZhaoYunhao_1220025803, proficient in git, familiar with c, python, cpp, master some front-end construction skills(html,css,javascript,react) and master knowledge of data structure, computer organization.
3. name, qualifications and strengths
4. ChenWen_1220022740, familiar with python, c, cpp, C sharp, etc. ,familiar backend construction, master knowledge of algorithms and  data structures.
### Team Leader:
QinJunshuo_1220022811 (Jason Chun)
- Rust, Python backend developer
- Currently working on HPC and Security
- Possesses extensive development experience

## Project Description
### Problem Diagnosis
#### High Level Problem
Under MUST's network, developers and researchers may experience slow access to certain resources, such as software packages (Linux packages), scientific tools (HPC kits, Conda packages, etc.), or even model files (e.g., LLaMA, Qwen from Hugging Face). This is largely due to network congestion caused by the high volume of users on campus. By establishing a local mirror within the campus for researchers to access, these issues can be significantly alleviated. This solution would also reduce the strain on the campus network's external bandwidth. \
Moreover, MUST's SuperComputing Station is in development, hence a mirror is highly required.

#### Specific Issues
1. **Limited outbound bandwidth**: The school's outbound bandwidth is fixed, so a campus mirror is needed to alleviate external usage.
2. **Scarcity of hardware resources**: The school lacks sufficient large-scale storage devices.
3. **High management costs**: The maintenance of the mirror site requires professionals to carry it out.

### Proposed Treatment

1. **Establish a Local Mirror**: Set up a campus mirror to provide on-campus access and validated off-campus access, significantly improving resource access speeds for developers and researchers while alleviating the strain on the school's limited outbound bandwidth.

2. **Optimize Resource Allocation**: Implement a distributed deployment solution that divides the architecture into a supervisor and multiple workers, maximizing the use of available hardware resources and enabling efficient management of the mirror.
Moreover, we can support more hardware like arm, riscv or loongarch.  

3. **Develop a User-Friendly Admin Console**: Create a comprehensive graphical operation and maintenance system that simplifies management tasks, reducing the high management costs associated with maintaining the mirror site. This will make it easier for non-experts to operate and maintain the system effectively.

4. **Merics and Alert system**: Implement a robust metrics and alert system to monitor the performance and health of the local mirror. Track access speeds, resource usage, and potential bottlenecks in real time.Alerts will be configured to notify administrators of any anomalies or performance drops like Syncfailure, ensuring timely interventions.

### Functional Features
#### Simplified Deployment
- **Command Line Setup**: We provide a comprehensive CLI deploy interface for maintainer to setup the whole system.
- **Portable Setup**: We provide more portable setup method like Docker Images. Mirror site maintainer could use docker compose to setup supervisor and distributed workers. 

#### Fast Access Speed
- **Provide In-school Access**: This local access will facilitate seamless downloads of software packages, scientific tools, and model files, ultimately supporting a more efficient research and development environment. Additionally, regular updates to the local mirror will ensure that users have access to the latest versions and resources without the delays associated with external connections.

#### User-Friendly Frontend
- **Mirror Helper**: Offers detailed usage guidelines for each mirror.
- **Admin Console**: Provides a simple and efficient graphical operation and maintenance system, along with an alert interface.

#### Merics System
- **Access speed**: Evaluate the improvement of access speed by monitoring the loading time of users accessing the mirror website.
- **Access success rate**: Statistically calculate the proportion of users successfully accessing the mirror website to evaluate the availability of the website.
- **Content synchronization timeliness**: Monitor the synchronization frequency and delay of the mirror site and the original website content to ensure real-time content updates.

#### Business Value
- A cost-effective and efficient mirror system can be provided to cloud service providers like Huawei Cloud or used by schools to build internal network mirror systems. 
- In fact, we plan to **open source** it and offer it for free to everyone.

### User Experience
After setting up a mirror website in MUST: 
1. **User Friendly Website**: We offer an intuitive website and assistance tools to enhance the user experience, making it easy for users to navigate and utilize the available mirror repo.
2. **Fast access**: Users can quickly load and browse website content without long waiting times.
3. **High availability**: Users can smoothly access the website at any time and anywhere without encountering access failures or page loading failures.
4. **Seamless content access**: Users can access all content, including content that may be blocked or restricted on the original website.
5. **Secure connection**: User access data is transmitted through encrypted connections to ensure privacy and data security.
6. **Consistent user experience**: Whether users access the original website or the mirror website, the experience is consistent without any differences.

## Plan of Work
### Functionalities
**Goal**: Realize the basic functions of the mirror website, including synchronization, access, and management.
#### Synchronize upstream:
- **Task**: Implement the content synchronization function from the original website to the mirror website.
- **Time**: 3 weeks
- **Correlation**: This is the core function of the mirror website and must be implemented first.
#### Access function:
- **Task**: Ensure that users can access content through the mirror website.
- **Time**: 3 weeks
- **Correlation**: Depends on the synchronization function to ensure that users can access after content synchronization.
#### Management function(Parallel with "Access Function"):
- **Task**: Provide a basic management interface to allow administrators to view and manage the mirror website.
- **Time**: 3 weeks
- **Correlation**: Needs to be integrated with synchronization and access functions to ensure that administrators can manage these functions.
### Qualitative Property
#### Manageability

**Goal**: Realize the manageability of the mirror website and provide an external UI and automated management tools.

- **External UI**:
    - **Task**: Develop a user-friendly external UI to allow administrators to operate.
    - **Time**: 3 weeks
    - **Correlation**: Needs to be integrated with management functions to provide a more intuitive management interface.

- **Automated management**:
    - **Task**: Implement automatic update and manual intervention functions, and administrators can update with one click or handle problems manually.
    - **Time**: 2 weeks
    - **Correlation**: Needs to be integrated with synchronization and management functions to ensure the effectiveness of automated management.

#### High Availability

**Goal**: Ensure the mirror system remains highly available, minimizing downtime and providing continuous access to resources for users both on-campus and off-campus.

- **Redundancy**:
    - **Task**: Implement redundancy strategies, such as deploying backup servers or multiple instances across different locations, to prevent single points of failure.
    - **Time**: 4 weeks
    - **Correlation**: Needs to be integrated with load balancing and automated failover mechanisms to maintain service continuity during system failures or maintenance.

- **Load Balancing**:
    - **Task**: Set up load balancing mechanisms to distribute traffic evenly across multiple servers, ensuring consistent performance and preventing server overload.
    - **Time**: 3 weeks
    - **Correlation**: Requires integration with monitoring systems to ensure balanced resource usage and improve overall system stability.

- **Monitoring and Alerts**:
    - **Task**: Deploy real-time monitoring tools to track the health and performance of the mirror system, paired with an alert system to notify administrators of any potential issues before they lead to downtime.
    - **Time**: 2 weeks
    - **Correlation**: Integrates with metrics and alert systems to provide timely feedback for maintaining high availability.

#### Portability

**Goal**: Ensure the portability of the mirror website, separate the front end and back end, and be easy to migrate and expand.

- **Frontend and Backend separation**:
    - **Task**: Develop the front end and back end separately to ensure that they run independently.
    - **Time**: 1 week
    - **Correlation**: Needs to be integrated with all functions to ensure the portability of the system.
- **API design**:
    - **Task**: Design and implement back-end APIs for use by the front end.
    - **Time**: 1 week
    - **Correlation**: Needs to be integrated with front-end and back-end separation functions to ensure the availability of APIs.

#### Flexibility (additional)

**Goal**: Realize the flexibility of the system and support plug-ins and extension functions.
- **Plugin support**:
    - **Task**: Implement a plugin mechanism to allow adding and managing plugins.
    - **Time**: 2 weeks
    - **Correlation**: Needs to be integrated with management functions to ensure the availability of plugins.
- **Extension function**:
    - **Task**: Implement additional functions such as synchronizing binary files or reverse proxy services.
    - **Time**: 2 weeks
    - **Correlation**: Needs to be integrated with plugin support functions to ensure the availability of extension functions.
