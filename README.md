# testerbester
import time

class DeliverySystem:
    def __init__(self):
        self.packages = []
    
    def add_package(self, package):
        self.packages.append(package)
    
    def track_package(self, package_id):
        for package in self.packages:
            if package['id'] == package_id:
                return package
        return None

    def update_package_status(self, package_id, status):
        package = self.track_package(package_id)
        if package:
            package['status'] = status
        else:
            print(f"Package with ID {package_id} not found.")
    
    def list_packages(self):
        for package in self.packages:
            print(f"ID: {package['id']} | Status: {package['status']}")

if __name__ == "__main__":
    delivery_system = DeliverySystem()

    while True:
        print("Delivery System Menu:")
        print("1. Add Package")
        print("2. Track Package")
        print("3. Update Package Status")
        print("4. List Packages")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            package_id = input("Enter package ID: ")
            package_status = "In Transit"
            delivery_system.add_package({"id": package_id, "status": package_status})
            print(f"Package with ID {package_id} added.")

        elif choice == "2":
            package_id = input("Enter package ID to track: ")
            package = delivery_system.track_package(package_id)
            if package:
                print(f"Package ID: {package['id']} | Status: {package['status']}")
            else:
                print(f"Package with ID {package_id} not found.")

        elif choice == "3":
            package_id = input("Enter package ID to update status: ")
            package_status = input("Enter new status: ")
            delivery_system.update_package_status(package_id, package_status)
            print(f"Status updated for package ID {package_id}.")

        elif choice == "4":
            print("List of Packages:")
            delivery_system.list_packages()

        elif choice == "5":
            print("Exiting the Delivery System.")
            break

        else:
            print("Invalid choice. Please enter a valid option.")

        time.sleep(1)  # To simulate the real-time nature of package tracking.
