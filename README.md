# Apex_notepad
1) file menu options:new , open and save,share,sync, profile 2)profile management 3) exit confirmation 4)email sharing
   tk.Label(profile_window, text="Phone:").grid(row=2, column=0)
        phone_entry = tk.Entry(profile_window)
        phone_entry.grid(row=2, column=1)

        # Save button for profile information
        def save_profile():
            profile_data = {
                "Name": name_entry.get(),
                "Email": email_entry.get(),
                "Phone": phone_entry.get()
            }
            with open("profile.pkl", "wb") as profile_file:
                pickle.dump(profile_data, profile_file)
            messagebox.showinfo("Apex Note", "Profile saved successfully!")

        tk.Button(profile_window, text="Save", command=save_profile).grid(row=3, column=0, columnspan=2)

        # Load existing profile data if available
        if os.path.exists("profile.pkl"):
            with open("profile.pkl", "rb") as profile_file:
                profile_data = pickle.load(profile_file)
                name_entry.insert(0, profile_data.get("Name", ""))
                email_entry.insert(0, profile_data.get("Email", ""))
                phone_entry.insert(0, profile_data.get("Phone", ""))

    def exit_app(self):
        if messagebox.askokcancel("Exit", "Do you really want to exit?"):
            self.root.destroy()


if __name__ == "__main__":
    root = tk.Tk()
    app = ApexNote(root)
    root.mainloop()
