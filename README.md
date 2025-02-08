# rokdey
class Customer:
    def __init__(self, name, email, mobile, address, consultation_type):
        self.name = name
        self.email = email
        self.mobile = mobile
        self.address = address
        self.consultation_type = consultation_type


class Consultant:
    def __init__(self, name, expertise, contact):
        self.name = name
        self.expertise = expertise
        self.contact = contact

    def show_profile(self):
        return f"Name: {self.name}\nExpertise: {self.expertise}\nContact: {self.contact}"


def get_customer_details():
    print("\n--- Welcome to Rokdey Home & Company Consultant Service ---")
    name = input("Enter your name: ")
    email = input("Enter your email: ")
    mobile = input("Enter your mobile number: ")
    address = input("Enter your address: ")
    consultation_type = input("Choose Consultation Type (House/Company): ").strip().lower()

    return Customer(name, email, mobile, address, consultation_type)


def choose_consultation_mode():
    print("\nFor consultation, choose an option:")
    print("1. Meeting with Consultant")
    print("2. Call to Consultant")
    choice = input("Enter your choice (1/2): ")
    return choice


def display_consultants(consultants):
    print("\nAvailable Consultants:")
    for idx, consultant in enumerate(consultants, start=1):
        print(f"{idx}. {consultant.show_profile()}")
    
    choice = int(input("Choose a consultant (Enter number): "))
    return consultants[choice - 1]


def main():
    customer = get_customer_details()

    # Sample consultant profiles
    consultants = [
        Consultant("John Doe", "House Consultant", "john@example.com"),
        Consultant("Jane Smith", "Company Consultant", "jane@example.com"),
        Consultant("Michael Lee", "Real Estate Advisor", "michael@example.com")
    ]

    choice = choose_consultation_mode()

    if choice == "1":
        print("\nYou have chosen to meet with a consultant.")
        selected_consultant = display_consultants(consultants)
        print(f"\nMeeting scheduled with {selected_consultant.name}.")
    elif choice == "2":
        print("\nYou have chosen to call a consultant.")
        selected_consultant = display_consultants(consultants)
        print(f"\nCalling {selected_consultant.name} at {selected_consultant.contact}...")
    else:
        print("\nInvalid choice. Please restart the process.")

    print("\nYour request is successfully completed!")


if __name__ == "__main__":
    main()
