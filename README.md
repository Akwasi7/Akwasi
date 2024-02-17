package Shopping;

import Shopping.ElementNotFoundException;
import Shopping.EmptyCollectionException;
import org.junit.Test;
import static org.junit.Assert.*;
import org.junit.Before;

/**
 * @version Spring 2019
 * @author Paul Franklin, Kyle Kiefer
 * Modified Fall 2022 by Bruce Long
 */
public class ShoppingListArrayListTest {

    private ShoppingListArrayList instance;

    /**
     * Initialize instance and entries
     */
    @Before
    public void setupTestCases() {
        instance = new ShoppingListArrayList();
    }

    /**
     * TODO To Complete the test of add method.
     */
    @Test
    public void testAdd() {
        //Create grocery objects and a shopping list instance
        Grocery item1 = new Grocery("Harry Potter", "book", 3, 15.5f, 2);
        Grocery item2 = new Grocery(item1);
        item2.setQuantity(3);
 
        instance = new ShoppingListArrayList();

        // TODO test the add method for the case of adding a new item (item1) 
        // into the list instance 
        // Be sure that 1) size is increased by 1 and 
        //              2) the first item in the list is the same as in the 
        //                 reference variable, item1 
        






        
        // TODO test the "combine" feature of the add method
        // for the case of adding an existing entry, the item2
        // into the shopping list instance created in previous 
        // code block. The item2 has the same entry name as the item1.
        // Be sure that 1) size is not changed and 
        //              2) quantities are properly combined for the first item 
        //                 in the list.
        







        
        // Test creating and adding a new grocery object to the list
        // Be sure that 1) the shopping list has a proper number of items
        //              2)the list item in the list is the same as in the newly
        //                created grocery object
        Grocery item3 = new Grocery("Laugh in the Rains", "book", 3, 35.5f, 1);
        instance.add(item3);
        System.out.println("Test..." + instance.size());
        assertEquals(2, instance.size());
        try {
            assertEquals(0, item3.compareTo(instance.find(1)));
            assertEquals(item3.getQuantity(), instance.find(1).getQuantity());
        } catch (Exception ex) {
            fail("Unexpected exception in testAdd" + ex.getMessage());
        }
    }

    /**
     * TODO To Complete the test of remove method.
     */
    @Test
    public void testRemove() {
        //Create grocery objects
        Grocery item1 = new Grocery("Harry Potter", "book", 3, 15.5f, 2);
        Grocery item2 = new Grocery("Hunger Game", "book", 3, 10.5f, 3);
        
        // Construct a shopping list
        instance = new ShoppingListArrayList();
        instance.add(item1);
        instance.add(item2);
        assertEquals(2, instance.size());
        boolean isRemoved;
        // TODO test the remove method for an existing entry, item1
        // Be sure that 
        //   1) the returned value from the remove method is true
        //   2) the shopping list is decreased by 1
        //   3) the item being removed cannot be found in the shopping list
        







        // TODO test the remove method for a non-existing entry 
        // Be sure that 
        //   1) the returned value from the remove method is false
        //   2) the shopping list is not changed
        





        
        // Construct a case that the shopping list becomes empty
        isRemoved = instance.remove(item2);
        assertTrue(isRemoved);
        assertEquals(0, instance.size());
        
        // Test the remove method when the shopping list is empty
        isRemoved = instance.remove(item2);
        assertFalse(isRemoved);
        assertEquals(0, instance.size());
    }

    /**
     * TODO Complete the test of find method.
     */
    @Test
    public void testFind() {
        //Create grocery objects
        Grocery item1 = new Grocery("Harry Potter", "book", 3, 15.5f, 2);
        Grocery item2 = new Grocery("Hunger Game", "book", 3, 10.5f, 3);
        
        // Construct an empty shopping list
        instance = new ShoppingListArrayList();
        
        // TODO Test the case of finding a grocery object when the shopping 
        // list is empty.  Be sure that an EmptyCollectionException is thrown.








        
        // Add item1 and item2 into the shopping list
        instance.add(item1);
        instance.add(item2);
        assertEquals(2, instance.size());
        
        // TODO Test the case of finding a grocery object when the index is 
        // larger than the shopping list size.  Be sure that an 
        // IndexOutOfBoundsException instance is thrown.







        
        // Test the case of finding a grocery object when the index is negative
        try {
            Grocery item = instance.find(-5);
            fail("Should not get here in testFind with index of " + item);
        } catch (IndexOutOfBoundsException e) {
            assertTrue(e instanceof IndexOutOfBoundsException);
        } catch (Exception ex) {
            fail("General exception should not occur in testFind - " + 
                    ex.getMessage());
        }
        
        // Test the case of finding a grocery object when the index is valid
        try {
            Grocery item = instance.find(0);
            assertEquals(0, item1.compareTo(item));
            assertEquals(2, instance.size());
        } catch (Exception ex) {
            fail("General exception should not occur in testFind - " + 
                    ex.getMessage());
        }
    }

    /**
     * Test of indexOf method.
     */
    @Test
    public void testIndexOf() {
        //Create grocery objects
        Grocery item1 = new Grocery("Harry Potter", "book", 3, 15.5f, 2);
        Grocery item2 = new Grocery("Hunger Game", "book", 3, 10.5f, 3);
        
        // Construct an empty shopping list
        instance = new ShoppingListArrayList();
        
        // Check the indexOf method when the shopping list is empty
        try {
            int index = instance.indexOf(item1);
        } catch (Exception e) {
            assertTrue(e instanceof ElementNotFoundException);
        }
        
        // Add grocery items into the shopping list
        instance.add(item1);
        instance.add(item2);
        
        // Check the indexOf method when the grocery item appears in the list
        try {
            assertEquals(1, instance.indexOf(item2));
            assertEquals(0, instance.indexOf(item1));
        } catch (Exception e1) {
            fail("Shouldn't get here in testIndexOf" + e1.getMessage());
        }
        
        // Check the indexOf method when the grocery item does not appear in 
        // the list
        try {
            Grocery item3 = new Grocery("Aladin", "book", 3, 15.5f, 2);
            int index = instance.indexOf(item3);
        } catch (Exception e2) {
            assertTrue(e2 instanceof ElementNotFoundException);
        }
        
        // Check the indexOf method when the grocery item is null
        try {
            Grocery obj = null;
            int index = instance.indexOf(obj);
        } catch (Exception e3) {
            assertTrue(e3 instanceof ElementNotFoundException);
        }
    }

    /**
     * Test of contains method.
     */
    @Test
    public void testContains() {
        //Create grocery objects
        Grocery item1 = new Grocery("Harry Potter", "book", 3, 15.5f, 2);
        Grocery item2 = new Grocery("Hunger Game", "book", 3, 10.5f, 3);
        
        // Construct a shopping list
        instance = new ShoppingListArrayList();
        
        // Check the contains method when the shopping list is empty
        assertFalse(instance.contains(item1));
        
        // Add grocery items into the shopping list
        instance.add(item1);
        instance.add(item2);
        
        // Check the contains method when the grocery item appears in the list
        assertEquals(2, instance.size());
        assertTrue(instance.contains(item2));
        
        // Check the contains method when the grocery item does not appear in the list
        Grocery item3 = new Grocery("Aladin", "book", 3, 15.5f, 2);
        assertFalse(instance.contains(item3));
        
        // Check the contains method when the grocery item is null
        Grocery obj = null;
        assertFalse(instance.contains(obj));
    }

    /**
     * Test of size method.
     */
    @Test
    public void testSize() {
        Grocery entry1 = new Grocery("Mayo", "Dressing / Mayo", 1, 2.99f, 1);
        instance = new ShoppingListArrayList();

        assertEquals(0, instance.size());

        instance.add(entry1);

        // Test increment
        assertEquals(1, instance.size());

        assertTrue(instance.remove(entry1));

        // Test decrement
        assertEquals(0, instance.size());
    }

    /**
     * Test of isEmpty method.
     */
    @Test
    public void testIsEmpty() {
        Grocery entry1 = new Grocery("Mayo", "Dressing / Mayo", 1, 2.99f, 1);
        instance = new ShoppingListArrayList();

        // Test empty
        assertTrue(instance.isEmpty());

        instance.add(entry1);

        // Test not empty
        assertFalse(instance.isEmpty());
    }
}
