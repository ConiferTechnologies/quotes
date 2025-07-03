# MIH CP Assignment Program - Statement of Work

## Project Overview

The MIH CP Assignment Program is a comprehensive healthcare provider routing and scheduling optimization system designed to efficiently assign Care Providers (CPs) and Emergency Medical Technicians (EMTs) to patients while minimizing travel time, maximizing continuity of care, and optimizing resource utilization.

## Executive Summary

This project will develop a custom optimization solution using Google OR-Tools to automate the daily assignment of healthcare providers to patients across multiple hospitals and outpatient locations. The system will replace manual scheduling processes with an intelligent, automated solution that considers multiple factors including provider expertise, patient history, geographic proximity, and workload balancing.

## Use Cases

### Primary Use Cases
1. **Daily Morning Assignments**: Automatically assign CPs to inpatients based on optimized routing and continuity factors
2. **Outpatient Scheduling**: Efficiently schedule EMTs and CPs for outpatient visits with geographic clustering
3. **Tuck-In Visit Assignments**: Optimize evening/night visit assignments for patients requiring basic care
4. **Dynamic Reassignment**: Real-time rescheduling when providers call out or patient conditions change
5. **Workload Management**: Ensure balanced assignments while respecting maximum visit limits

### Secondary Use Cases
1. **Performance Analytics**: Track provider efficiency and total time spent traveling
2. **Schedule Optimization**: Identify opportunities to reduce travel time and improve care delivery
3. **Resource Planning**: Forecast staffing needs based on patient volume and geographic distribution

## Functional Requirements

### Core Data Requirements
- **CP Daily Work Location**: Daily work locations (Beam, North, etc.), certifications, specializations
- **Patient Data**: GPS coordinates, Medical Record Numbers (MRN), admitting hospitals (CMC, Cab, etc.)
- **Care Constraints**: EMT-eligible patients, pediatric patients, medication restrictions (Lasix, Insulin), and PT acuity
- **Visit History**: Previous provider-patient interactions for continuity scoring

### Assignment Constraints
- **Provider Limits**: CPs maximum 4 inpatients (8 visits), EMTs/CPs maximum 6 outpatients
- **Scope Restrictions**: EMT limitations for specialized care requirements
- **Geographic Boundaries**: Multi-hospital system coverage area
- **Scheduling Windows**: Morning assignments, tuck-in visits, emergency reassignments

### PT Assignment Optimization Criteria
- **Daily PT to CP Match Score**: From -2 to 20 based on a static set of rules. The PT with the highest numerical match to a CP will be assigned
- **Continuity Scoring**: Previous day (+2), previous stay (+1) bonuses
- **Geographic Efficiency**: Distance-based scoring from provider base locations
- **Hospital Clustering**: Same-hospital visit bonuses (+5)
- **Travel Optimization**: Proximity-based scoring for sequential visits
- **Workload Balancing**: Penalty system for overloaded providers

## Technical Requirements

### System Architecture
- **Backend**: Python-based application using Google OR-Tools optimization engine
- **Database**: PostgreSQL for patient/provider data storage
- **API Layer**: RESTful services for data integration and mobile access
- **Web Interface**: React-based dashboard for schedule management
- **Integration**:  hospital information systems*

*Further context below under "Risk Assessment" 

### Security & Compliance
- **HIPAA Compliance**: Protected health information handling
- **Data Encryption**: At-rest and in-transit encryption
- **Access Controls**: Role-based authentication and authorization
- **Audit Logging**: Complete action tracking for compliance

## Project Plan

### Phase 1: Foundation & Analysis (Weeks 1-3)
**Week 1: Requirements Analysis**
- Stakeholder interviews and workflow analysis
- Current state documentation and pain point identification
- Technical environment assessment
- Data source inventory and access planning

**Week 2: System Design**
- Architecture design and technology stack finalization
- Database schema design
- API specification development
- User interface mockups and workflow design

**Week 3: Development Environment Setup**
- Development infrastructure provisioning
- Google OR-Tools integration and testing
- Database setup and sample data loading
- Development team onboarding

### Phase 2: Core Development (Weeks 4-10)
**Week 4: Data Layer Implementation**
- Database schema implementation
- Data import/export functionality
- GPS coordinate integration
- Patient and provider data management

**Week 5: Optimization Engine Development**
- Google OR-Tools integration
- Scoring algorithm implementation
- Constraint definition and validation
- Initial optimization testing

**Week 6: Assignment Logic Implementation**
- Morning assignment algorithm
- Tuck-in visit optimization
- Outpatient scheduling logic
- Dynamic reassignment capabilities

**Week 7: API Development**
- RESTful API implementation
- Authentication and authorization
- Data validation and error handling
- Mobile-friendly endpoints

**Week 8: Testing & Optimization**
- Unit testing and integration testing
- Performance optimization
- Algorithm tuning with sample data
- Security testing and HIPAA compliance validation

### Phase 3: User Interface & Integration (Weeks 11-13)
**Week 9: Web Interface Development**
- Dashboard development
- Schedule management interface
- Provider and patient management screens
- Reporting and analytics views

**Week 10: System Integration**
- Hospital information system integration
- GPS and mapping service integration
- Mobile application development (if required)
- Third-party API integrations

**Week 11: End-to-End Testing**
- Full system testing with real data
- User acceptance testing
- Performance testing under load
- Security penetration testing

### Phase 4: Deployment & Training (Weeks 14-16)
**Week 12: Deployment Preparation**
- Production environment setup
- Data migration planning and execution
- Backup and disaster recovery implementation
- Go-live planning and preparation

**Week 13: Training & Documentation**
- User training program delivery
- Administrator training
- Documentation completion
- Support procedure establishment

**Week 14: Go-Live & Support**
- Production deployment
- Go-live support and monitoring
- Issue resolution and system tuning
- Post-deployment optimization

## Deliverables

### Technical Deliverables
- **Optimization Engine**: Google OR-Tools based assignment system
- **Web Application**: Complete scheduling and management interface
- **Mobile Interface**: Web application fully usable and responsive on mobile
- **API Documentation**: Complete API specification and integration guide
- **Database**: Fully configured and optimized data storage solution

### Documentation Deliverables
- **User Manuals**: End-user and administrator guides
- **Technical Documentation**: System architecture and maintenance guides
- **Training Materials**: Video tutorials and quick reference guides
- **Deployment Guide**: Installation and configuration procedures

### Support Deliverables
- **30-Day Warranty**: Post-deployment bug fixes and optimization
- **Training Program**: Comprehensive user and administrator training
- **Knowledge Transfer**: Technical handoff to client IT team
- **Maintenance Plan**: Ongoing support and enhancement roadmap

## Budget Estimate

### Development Costs
- **Phase 1 (Foundation)**: 3 weeks, $27,000
- **Phase 2 (Core Development)**: 6 weeks, $54,000
- **Phase 3 (UI & Integration)**: 3 weeks, $27,000
- **Phase 4 (Deployment)**: 2 weeks, $18,000
- **Total Development**: $126,000

### Infrastructure Costs (Estimated Annually)
- **Cloud Hosting**: $2,000
- **Third-party APIs**: $2,000
- **Security & Compliance**: $10,000
- **Ongoing Support**: $67,500 (support and troubleshooting)
- **Total Estimated Annual**: $81,500

## Risk Assessment

### Technical Risks
- **Integration Complexity**: Hospital system integration challenges as 

Integration with Hospital IT systems often requires a series of security reviews, approvals, and is subject final approval by the Hospital CIO. Two possible work arounds are to build the system to a security specification such as SOC2 Type2 or HITRUST. The other option is to manually load the data into the routing application via a CSV download from the EMR or similar process. 

With either approach careful consideration needs to be made of the HIPAA constraints of each data point. PT GPS location, medication, and MRN are all directly identifiable information which would mean this system must meet HIPAA compliance. 
- **Data Quality**: Incomplete or inaccurate source(s) of data will render the system inoperable
- **HIPAA Compliance**: Healthcare data protection requirements

## Commercial Off-the-Shelf Options

While a custom solution using Google OR-Tools provides the best fit for the specific healthcare requirements, the following commercial alternatives were evaluated:

### Route Optimization Platforms
**Route4Me**
- Strengths: User-friendly interface, good basic routing optimization
- Limitations: Limited healthcare-specific features, basic scoring system
- Cost: $40-200/month per user
- Fit: 60% - Would require significant workarounds for continuity scoring

**OptimoRoute**
- Strengths: Advanced scheduling features, mobile apps
- Limitations: No healthcare provider continuity features
- Cost: $35-45/month per vehicle
- Fit: 55% - Limited customization for complex scoring requirements

**Workwave Route Manager**
- Strengths: Comprehensive fleet management, reporting
- Limitations: Designed for delivery/service, not healthcare continuity
- Cost: $49-99/month per user
- Fit: 50% - Would need extensive customization

### Field Service Management
**ServiceTitan**
- Strengths: Comprehensive field service management
- Limitations: Not designed for healthcare provider routing
- Cost: $99-199/month per user
- Fit: 40% - Healthcare workflows not supported

**FieldEdge**
- Strengths: Mobile-first design, scheduling optimization
- Limitations: No healthcare-specific features or compliance
- Cost: $79-149/month per user
- Fit: 45% - Missing critical healthcare requirements

### Enterprise Solutions
**Oracle Field Service**
- Strengths: Enterprise-grade, highly customizable
- Limitations: Expensive, complex implementation
- Cost: $150-300/month per user
- Fit: 75% - Could be customized but at significant cost

**Salesforce Field Service**
- Strengths: Integrated CRM, mobile optimization
- Limitations: Requires extensive customization for healthcare
- Cost: $75-150/month per user
- Fit: 65% - Platform could support requirements with development

### Recommendation
None of the commercial off-the-shelf solutions adequately address the specific healthcare provider continuity requirements, complex multi-factor scoring system, or HIPAA compliance needs outlined in the RFQ. The custom Google OR-Tools solution provides the best balance of functionality, cost-effectiveness, and regulatory compliance for this specialized healthcare routing application.