@startuml
left to right direction
actor Admin
actor "Normal User" as NormalUser
actor "Company User" as CompanyUser

rectangle "Jobst Webapp*" {
    usecase "Manage Users" as ManageUsers
    usecase "Create CV" as CreateCV
    usecase "Edit CV" as EditCV
    usecase "Delete CV" as DeleteCV
    usecase "Analyze CV" as AnalyzeCV
    usecase "View CV" as ViewCV
    usecase "Login" as Login
    usecase "Register" as Register
    usecase "Reset Password" as ResetPassword
    usecase "Add Job Post" as AddJobPost
    usecase "Get Feed of Candidats" as GetCandidat
    usecase "Show Status Bar" as StatusBar

    Admin --> ManageUsers
    Admin --> StatusBar
    NormalUser --> CreateCV
    CreateCV .> StatusBar :include
    NormalUser --> EditCV
    EditCV .> StatusBar :include
    NormalUser --> DeleteCV
    NormalUser --> ViewCV
    NormalUser --> Login
    Login .> (User Not Found) :extend
    NormalUser --> Register
    NormalUser --> ResetPassword
    CompanyUser --> AnalyzeCV
    CompanyUser --> ViewCV
    CompanyUser --> AddJobPost
    CompanyUser --> Login
    CompanyUser --> Register
    CompanyUser --> ResetPassword
    CompanyUser --> GetCandidat
}
@enduml