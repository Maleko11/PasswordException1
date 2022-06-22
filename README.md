














public class PasswordException extends Exception
{
	public PasswordException(String message)
	{
		super(message);
	}
	
	public boolean validatePassword(String password)throws PasswordException
	{
		boolean isTrue = true;   
		int  spacial = 0; 
		int  number = 0;
		
		if(password.length() < 10)
		{
			isTrue = false;
			throw new PasswordException("The password must be at least 10 characters long");
		}
		
		for(int x = 0; x < password.length();x++)
		{
			if(password.charAt(x) == '@' || password.charAt(x) == '#' || password.charAt(x) == '$' || password.charAt(x) == '^'||password.charAt(x) == '*'||password.charAt(x) == '&' )
			{
				spacial = spacial + 1;
			}
			
			if(Character.isDigit(password.charAt(x)) == true)
			{
				number = number + 1;
			}
		}
		
		if(number  < 2)
		{
			isTrue = false;
			throw new PasswordException("The password must have at least 2 numbers");
		}
		if(spacial < 2)
		{
			isTrue = false;
			throw new PasswordException("The password must have at least 2 special characters @#$^&");
		}
		
		return isTrue;
	}
	
}
