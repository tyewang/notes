# General Python Guidelines

Unlike PEP-8, these rules do not concern style or formatting. Instead, they are simply a collection of rules of thumb.

## General
- Always prefix helper functions/methods with `_`
- Don't call `_` functions outside of the module they are contained in. _This includes tests_.

## Testing
- Don't mock or patch `_` functions in tests.
- Don't test `_` functions.
- If you are using `nosetests` or `UnitTest`, organize your tests as follows:
  - The test file should be parallel to the module. This means if you are writing tests for `my_awesome_code.py`, put the tests in `test/test_my_awesome_code.py`
  - Test cases (the classes in the test file) should be used to organize tests into sections.
  - Tests (the functions in each class) should have descriptive names and should test a _single_ scenario.
  - BAD:
    ```
    ListTest(TestCase):

      def test_list(self):
        my_list = []

        my_list.append('a')
        self.assertIn('a', my_list)
        self.assertEqual(len(my_list), 1)

        my_list.extend(['b', 'c'])
        self.assertIn('b', my_list)
        self.assertIn('c', my_list)
        self.assertEqual(len(my_list), 3)

        my_list.remove('c')
        self.assertNotIn('c', my_list)
        self.assertEqual(len(my_list), 2)
    ```
  - GOOD:
    ```
    AppendTest(TestCase):

      def test_appends_value_to_list(self):
        my_list = []
        my_list.append('a')

        self.assertIn('a', my_list)
        self.assertEqual(len(my_list), 1)

    ExtendTest(TestCase):

      def test_appends_elements_to_list(self):
        my_list = ['a']
        my_list.extend(['b', 'c'])
        self.assertIn('b', my_list)
        self.assertIn('c', my_list)
        self.assertEqual(len(my_list), 3)

    RemoveTest(TestCase):

      def test_removes_value_from_list(self):
        my_list = ['a', 'b', 'c']
        my_list.remove('c')
        self.assertNotIn('c', my_list)
        self.assertEqual(len(my_list), 2)
    ```
